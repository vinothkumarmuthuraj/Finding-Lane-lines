# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of 11 steps.

1) Converted the RGB image into gray scale image
2) Convert RGB to HSV
3) Darken the Gray scale
4) Isolate yellow and white in HSV to produce a yellow mask and white mask
5) Combine yellow and white masks with bitwise OR
6) And again combined the mask with gray scale
7) Apply slight Gaussian blur
8) Perform canny edge detection
9) Define the region of interest using four sided polygon
10) Hough lines
11) Extrapolate the lines and apply them to original image 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 
This draw_lines function basically to draw a one continuous line on right and left lane from collection of lines. 
consolidated the collections of lines for each side of lane and to extrapolate that line to bottom edge of immage and to a point near to the center of image.
1) created a 2D array using hough lines and 2) calculated the slope and intercept for collinear points, 3) then stored them in a list and found out the max and min slope line, 4) then created 4 empty lists for left and right slopes and intercepts,6) then appending the x1,y1,x2,y2 in a new 2D array.  

If you'd like to include images to show how the pipeline works, here is how to include an image: 
The output images are available in the folder in the name 1,2,3,4,5,6 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


Hough parameters modification
Color sensitivity
Not properly identifying lanes with even small curvy roads


### 3. Suggest possible improvements to your pipeline

Better tuned hough transform parameters
Calculating region of interest automatically

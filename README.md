# **Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

1- convert colored image to gray scare. This conversion will convert our 3 channel image to one channel image.

2- Apply gaussian blure. This step will help reduce the noise in the image and smooth out the image to reduce the false edge detaction.

3- Apply canny edge detection. This step will extract the edges from the gray image(sudden changes in color).

4- Extract region of intreast. This step will remove the part of the image which will have a low probability of having the line we are intrested in locating

5- Apply hough lines to detect possible lines. 

6- Draw line. In this step the the lines that are found from hough line are seperated to left and right line, 
extrapolate to get a single line and drawn on the image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() adding the connect_lines. This function will first calculate the slope of the line for each of the lines fround by lough line.
Base on the slope of the line the points are assigned to left of right line. If the slope of the is not between plus minus 30-43 is rejected. After the lines are idendified a single slope and point on the line is calculated. The slope and the point is then used to calculate the beginnign and end point of a line.
   

Sample output:



![alt text![]](test_images_output/solidYellowLeft.jpg)[sample output 1]
![alt text![]](test_images_output/solidWhiteRight.jpg)[sample output 2]
![alt text![]](test_images_output/solidYellowCurve.jpg)[sample output 3]

### 2. Identify potential shortcomings with your current pipeline

This is a very basic lane detection algorithm which has a lot of short coming including:

1- Lake of robustness to change of lighting

2- Not being able to correctly detect curved roads

3- detecting line in just a limited area of the image

4- detecting only single line

### 3. Suggest possible improvements to your pipeline

1- Use of color thresholding to improve the lane detection


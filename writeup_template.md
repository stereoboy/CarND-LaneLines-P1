#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/result_solidWhiteCurve.jpg "Result"
[image2]: ./test_images/result_solidYellowCurve.jpg "Result"
[image3]: ./test_images/result_whiteCarLaneSwitch.jpg "Result"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps.

1. grayscale conversion
2. gaussian blurring
3. edge detection
4. roi masking for left, right individually
5. hough line detection separately on left, right roi
6. merge left, right

In order to handle left, right roi separately, I made new functions: draw_lines_v2() and hough_lines_v2().

In draw_lines_v2(), lines are filtered with respect to slope value. The filter-related parameter is hard-coded. -0.8, -0.5 for left roi, 0.5, 0.8 for right roi.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![./test_images/result_solidWhiteCurve.jpg][image1]
![./test_images/result_solidYellowCurve.jpg][image2]
![./test_images/result_whiteCarLaneSwitch.jpg][image3]


###2. Identify potential shortcomings with your current pipeline

Hard-coded values can occurs errors or malfunctions if any exceptional slope of lines included in lanes enters.

###3. Suggest possible improvements to your pipeline

By analysing stastical information based slopes, line-length and line-position, noise lines can be filtered.

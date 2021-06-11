Finding Lane Lines on the Road

Goals
The goals / steps of this project are the following:

Make a pipeline that finds lane lines on the road
Reflect on your work in a written report


## Aims
The main properties that the lane marking (or boundary) detection techniques should possess are:
1. The quality of lane detection should not be affected by shadows, which can be cast by trees, buildings, etc.
2. It should be capable of processing the painted and unpainted roads. It should handle curved roads rather than
   assuming that the roads are straight.
3. It should use the parallel constraint as a guidance to improve the detection of both sides of lane markings 
   (or boundaries) in the face of noises in the images.
   
## Reflection
1. Convert the image to grey scale we do this because edge detection will not require the color information 
2. Then apply Gaussian function for noise reduction in the image 
3. Pass the Gaussian blured image to a canny edge detector with upper and lower threshold values this double thresholding  helps in detecting only the images required 
4. the image is then cropped so that the mask applied will hide all other edges except for that of the lane 
5. this masked image is then hough transformed for full feature extraction is , An image with lines drawn on
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by

1. reshaping the lines fit to a 2d matrix
2. then creating an array of slopes
3. remove nan and infinity from the lists
4. converting lines into list of points
5. moving all points with negative slopes into right "lane"
6. moving all points with negative slopes into left "lane"
7. calculate polynomial fit for the points in each lane
8. use new curve function f(y) to calculate x values
Shortcomings
1. much of the efficiency of the Hough transform is dependent on the quality of the input data: the edges must be detected        well for the Hough transform to be efficient. 
2. the Hough transform must be used with great care to detect anything other than lines or circles.
3. the pipeline will not work well with a noisy images and selection for threshold values for the canny edge detector is a        trial and error metod
4  A robust lane-detectionand- tracking algorithm deals with the challenging scenarios such as a lane curvature, 
   lane changes, worn lane markings and emerging, merging, ending, and splitting lanes. our algorithm will not deal with    many of these 
Improvements
1. using a neural network for threshold determination for canny edge detection
2. using a neural network for hough transform approximations 
3. adding lane center detection 
4. better curve fitting algorithm selection 
About
Udacity-Project-1

Resources
 Readme
Releases
No releases published
Packages
No packages published
Languages
Jupyter Notebook
100.0%

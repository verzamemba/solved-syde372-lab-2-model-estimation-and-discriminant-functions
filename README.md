Download Link: https://assignmentchef.com/product/solved-syde372-lab-2-model-estimation-and-discriminant-functions
<br>



<h1>1           Purpose</h1>

This lab examines the areas of statistical model estimation and classifier aggregation. Model estimation will be performed by implementing parametric and non-parametric estimators. Aggregation is introduced by combining several simple linear discriminants into one more powerful classifier.

<h1>2           Model Estimation 1-D case</h1>

For this part of the lab, use the data set provided on the course homepage: http://ocho.uwaterloo.ca/⇠pfieguth/Teaching/372/lab2 1.mat There are two data sets:

<ul>

 <li>variable <em>a </em>– a bunch of Gaussian samples, <em>µ </em>= 5, = 1.</li>

 <li>variable <em>b </em>– a bunch of Exponential samples, = 1.</li>

</ul>

Do the following steps for <strong>each </strong>data set:

<ol>

 <li><strong>Parametric Estimation – Gaussian</strong>: Assume that the unknown density is Gaussian; this leaves two parameters to estimate: the mean and the variance. Use Maximum Likelihood to estimate these parameters. Plot the resulting estimated ˆ<em>p</em>(<em>x</em>) superimposed on the true <em>p</em>(<em>x</em>).</li>

 <li><strong>Parametric Estimation – Exponential</strong>: Assume that the unknown density is Exponential; this leaves one parameter to estimate: parameter . Use Maximum Likelihood to estimate this parameter. Plot the resulting estimated ˆ<em>p</em>(<em>x</em>) superimposed on the true <em>p</em>(<em>x</em>).</li>

 <li><strong>Parametric Estimation – Uniform</strong>: Assume that the unknown density is Uniform; this leaves two parameters to estimate: parameters <em>a </em>and <em>b</em>. Use Maximum Likelihood to estimate these parameters. Plot the resulting estimated ˆ<em>p</em>(<em>x</em>) superimposed on the true <em>p</em>(<em>x</em>).</li>

 <li><strong>Non-parametric estimation</strong>: Estimate the density using the Parzen method. Use Gaussian windows having standard deviations of 0.1 and 0.4. Generate two plots, one for each standard deviation. Plot the true density on top of the estimated density.</li>

</ol>

For each of the two data sets, which of the estimated densities is closest to the original? Give a qualitative comparison of the results. In general, is it possible to always use a parametric approach? When is it better to use a parametric method? When is the non-parametric approach preferred?

<h1>3           Model Estimation 2-D case</h1>

For this part of the lab, use the data set provided on the course homepage: http://ocho.uwaterloo.ca/⇠pfieguth/Teaching/372/lab2 2.mat

Here we will see the full power of the non-parametric approach. Data points for the three classes are stored in (<em>x,y</em>) format in variables <em>al</em>, <em>bl</em>, and <em>cl</em>.

<ol>

 <li><strong>Parametric estimation:</strong></li>

</ol>

Assume that each cluster is normally (Gaussian) distributed. Using the data, compute the sample mean and sample covariance of each cluster. Since plotting multiple 2D distributions is messy, instead find and plot the ML classification boundaries. Show the cluster data, superimposed with the classification boundaries, on the plot.

<ol start="2">

 <li><strong>Non-parametric estimation:</strong></li>

</ol>

Use a Gaussian Parzen window ( <sup>2 </sup>= 400) on the learning data to estimate a PDF for each cluster. Apply an ML classifier to the estimated PDFs and plot the classification boundaries together with the cluster data.

(Matlab code to implement 2D Parzen windows has been provided on the course website.)

Give a qualitative comparison of the classification results. In general, is it possible to always use a parametric approach? When is it better to use a parametric method? When is the non-parametric approach preferred?

<h1>4           Sequential Discriminants</h1>

For this part of the lab, use the data set provided on the course homepage:

http://ocho.uwaterloo.ca/⇠pfieguth/Teaching/372/lab2 3.mat

Points for the two classes are stored in (<em>x,y</em>) format in variables <em>a </em>and <em>b</em>.

What we want to do is to develop a <em>sequential </em>classifier. For any given discriminant <em>G</em>, we can use the entire data set to work out the following probabilities:

<em>P</em>(true class is <em>C<sub>i</sub></em>|<em>G </em>says <em>C<sub>k</sub></em>)

For a good sequential classifier, what we want are discriminants that get some part of some class exactly right, so that

<em>P</em>(true class is <em>C<sub>i</sub></em>|<em>G </em>says <em>C<sub>i</sub></em>) = 1

for at least <em>one </em>class <em>C<sub>i</sub></em>.

Here’s what we’ll do:

<ol>

 <li>Let <em>a </em>and <em>b </em>represent the data points in classes <em>A </em>and <em>B</em>. Let <em>j </em>= 1.</li>

 <li>Randomly select one point from <em>a </em>and one point from <em>b</em></li>

 <li>Create a discriminant <em>G </em>using MED with the two points as prototypes</li>

 <li>Using all of the data in <em>a </em>and <em>b</em>, work out the confusion matrix entries <em>n<sub>aB </sub></em>= #times <em>G </em>classifies a point from <em>a </em>as class <em>B</em></li>

</ol>

<em>n<sub>bA </sub></em>= #times <em>G </em>classifies a point from <em>b </em>as class <em>A</em>

<ol start="5">

 <li>If <em>n<sub>aB </sub></em>= 06 and <em>n<sub>Ba </sub></em>= 06 then no good, go back to step 2.</li>

 <li>This discriminant is good; save it as</li>

</ol>

<em>G</em><em>j </em>= <em>G, n</em><em>aB,j </em>= <em>n</em><em>aB, n<sub>bA,j </sub></em>= <em>n<sub>bA </sub></em>Let <em>j </em>= <em>j </em>+ 1.

<ol start="7">

 <li>If <em>n<sub>aB </sub></em>= 0 then remove those points from <em>b </em>that <em>G </em>classifies as <em>B</em>.</li>

 <li>If <em>n<sub>bA </sub></em>= 0 then remove those points from <em>a </em>that <em>G </em>classifies as <em>A</em>.</li>

 <li>If <em>a </em>and <em>b </em>still contain points, go back to step 2.</li>

</ol>

At this point we have a sequence of discriminants, each of which classifies some part of the problem perfectly. The overall classifier for some given point <em><u>x </u></em>is sequential, passing through <em>G</em><sub>1</sub><em>,G</em><sub>2</sub><em>,… </em>until a classification is made:

<ol>

 <li>Let <em>j </em>= 1</li>

 <li>If <em>G<sub>j </sub></em>classifies <em><u>x </u></em>as class B and <em>n<sub>aB,j </sub></em>= 0 then “Say Class B” If <em>G<sub>j </sub></em>classifies <em><u>x </u></em>as class A and <em>n<sub>bA,j </sub></em>= 0 then “Say Class A”</li>

 <li>Otherwise <em>j </em>= <em>j </em>+ 1 and go back to step 2.</li>

</ol>

<h2>Deliverables</h2>

<ol>

 <li>Learn three sequential classifiers, and for each one plot the resulting classification boundary along with the data points.</li>

 <li>If we test our classifier on the training data, what will its probability of error be? Discuss.</li>

 <li>In the above development we did not limit the number of sequential classifiers. Suppose we limit the sequential classifier to <em>J </em>classifiers <em>G</em><sub>1</sub><em>,…,G<sub>J</sub></em>. We want to see how the experimental error rate varies with <em>J</em>. For each value of <em>J </em>= 1<em>,</em>2<em>,…,</em>5, learn a sequential classifier 20 times to calculate the following:

  <ul>

   <li>the average error rate</li>

   <li>minimum error rate</li>

   <li>maximum error rate</li>

   <li>standard deviation of the error rates</li>

  </ul></li>

</ol>

Produce a plot showing these results as a function of <em>J</em>.

In our sequential classifier, we assumed that we could keep looking indefinitely for a classifier that would classify elements of some class perfectly. How might the results of the sequential classifier di↵er if I limited the number of point pairs that you could test?

<h1>5           Report</h1>

Include in your report:

<ul>

 <li>A brief introduction.</li>

 <li>Discussion of your implementations and results.</li>

 <li>Printouts of pertinent graphs (properly labeled).</li>

 <li>M-files for each section.</li>

 <li>Include responses to all questions.</li>

</ul>

A brief summary of your results with conclusions
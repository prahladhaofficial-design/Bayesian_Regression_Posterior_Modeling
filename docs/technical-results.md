# Technical Results


FOML-PA2-Calculations and Main Results
1 Bayesian Regression Calculations
Model Structure & Prior
Given:
y = sin(2x) + ,   N (0, 0.12)
With:
y(x; w) = w(x), w  N (0, I)
Where the basis vector:
(cid:18) (x   )2 (cid:19)
 (x) = 1,  (x) = exp  j , j = 1, . . . , 24
0 j 22
with  evenly spaced on [0, 1].
j
Sequential Bayesian Update
At step i, the posterior mean m and covariance S are updated as:
i i
S1 = S1 + (x )(x )
i i1 i i
S = (S1)1
i i
m = S (cid:0) S1 m + y (x ) (cid:1)
i i i1 i1 i i
where  = 1/0.12 = 100.
Posterior Predictive Distribution
For a new input x ,
0
p(t | x , D) = N (cid:0) m(x ), s2(x ) (cid:1)
0 0 0 0
where
m(x ) = (x )m
0 0 N
1
s2(x ) = + (x )S (x )
0  0 N 0
2 Bias-Variance Trade-off Calculations
Ridge Regression
The weight vector for each of L datasets is:
N
w(l) = arg min (cid:88) (cid:16) y(l)  w(x(l)) (cid:17)2 + w2
i i 2
w
i=1
The closed-form solution:
w(l) = (cid:0)  + I (cid:1)1 y(l)
1


Bias-Variance Decomposition (explicitly required)
For a test input x:
(cid:104) (cid:105) (cid:16) (cid:17)2 (cid:104) (cid:105)
E (y  f(x))2 = f (x)  E [f(x)] + E (f(x)  E [f(x)])2 +2
D D D D
(cid:124) (cid:123)(cid:122) (cid:125) (cid:124) (cid:123)(cid:122) (cid:125)
Bias2 Variance
Where f (x) = sin(2x), f(x) is fitted from each dataset.
3 Discriminant Functions & Generative Models
Gaussian Naive Bayes: Manual Likelihood Calculation
For data sample x, class c:
log p(x|y = c) =  1 (cid:88) log(22 )  1 (cid:88) (x j   cj )2
2 cj 2 2
j j cj
where  , 2 are estimated from training data.
cj cj
Bernoulli Naive Bayes: Manual Class Probability
After binarization:
d
p(x|y = c) = (cid:89) xj (1   )1xj
cj cj
j=1
with Laplace smoothing:
#ones in feature j for class c + 1
 =
cj N + 2
c
Linear Discriminant Analysis (LDA): Analytic Solution
With means  ,  and pooled covariance :
0 1
w = 1(   )
1 0
b =  1 (cid:0) 1  1 (cid:1) + log  1
2 1 1 0 0
0
L2-Regularized LDA: Analytic Solution
Use regularized covariance  + I:
w = ( + I)1(   )
reg 1 0
Computational Complexity
GNB/BNB: O(nd) fit, O(cd) predict
LDA/L2-LDA: O(nd2 + d3) fit, O(cd2) predict
2

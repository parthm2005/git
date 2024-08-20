### Problems 1 : Insertion sort on small arrays in merge sort
***
Although merge sort runs in Θ(n lg n) worst-case time and insertion sort runs in Θ(n^2) worst- case time, the constant factors in insertion sort make it faster for small n. Thus, it makes sense to use insertion sort within merge sort when subproblems become sufficiently small. Consider a modification to merge sort in which n/k sublists of length k are sorted using insertion sort and then merged using the standard merging mechanism, where k is a value to be determined.

a. Show that the n/k sublists, each of length k, can be sorted by insertion sort in Θ(nk) worst-case time.

b. Show that the sublists can be merged in Θ(n lg (n/k) worst-case time.

c. Given that the modified algorithm runs in Θ(nk + n lg (n/k)) worst-case time, what is
the largest asymptotic (Θnotation) value of k as a function of n for which the modified
algorithm has the same asymptotic running time as standard merge sort?

d. How should k be chosen in practice?

### `Answer`
**(a)** T(n) = (n/k)\*Θ(k<sup>2</sup>) = Θ(nk)  

**(b)** If there are n/k sublists, then the height of the tree formed will be lg(n/k). And at each level of the tree, the complexity of
merging is Θ(n). So the worst case to merge the sublists is Θ(n lg(n/k)).  

**(c)** Θ(nk + nlg(n/k)) = Θ(nk + nlgn - nlgk)) should be equal to Θ(nlgn)  
To satisfy this, `k` cannot grow faster than `lgn`, otherwise `nk` term will run worse than `Θ(nlgn)`. So `k <= Θ(lgn)` to satisfy the above condition.
So largest value of `k = lgn`.  

**(d)** Time complexity of insertion sort = c<sub>1</sub>n<sup>2</sup> and the time complexity of merge sort is c<sub>2</sub>nlgn.  
To find the value of k  
c<sub>1</sub>k<sup>2</sup> <= c<sub>2</sub>klgk  
k <= (c<sub>2</sub>/c<sub>1</sub>)lgk  
Now we can check manually by putting different values of k.



### Problems 2 : Correctness of bubblesort
***
Bubblesort is a popular sorting algorithm. It works by repeatedly swapping adjacent elements that are out of order.

### `Answer`
a. We also need to prove that the elements in the array are the original elements

b. **Before the cycle, the minimum element of the sub -group A [j ..] isA[j]** <br />
Initialization:At the beginning, there was only one element of the sub -array, which was the last element of A. <br />
Maintenance:Each iteration will compare the size of A [j] and a [j-1], and put the small one forward <br />
Termination:At the end of iteration, j = i, a [i] is the minimum element of sub -array A [i ..]<br />

c. **Before the cycle, A [1, I-1] is a sorted array, and less than equal to the element in A [i ..]**
Initialization:At the beginning, the sub -array was empty, and the cycle was unable to be established naturally <br />
Maintenance:Each iteration, A [i] will become a minimum element in A [i ..] <br />
Termination:At the end of iteration, i = n, we got a sorted array<br />

d. **bubblesort**The worst operation time and time**insertion sort**一All are θ (n^2), but in general**bubblesort**Will slowly, because it has a lot**swap**operate.


### Problems 3 : Correctness of Horner's rule
***
### `Answer`

**a.** Θ(n)

**b.**
Naive-Poly-Eval:

	y = 0
	for i = 0 to n
    	m = 1
    	for k = 1 to i
        	m = m·x
    	y = y + aᵢ·m
Running time is Θ(n2),Very slow

**c.** 

**Initialization:** 一There is no item at the beginning，y = 0 

**Maintenance:**According to the cycle unchanged, the I iteration is ended at the end

![](http://latex.codecogs.com/gif.latex?y=a_i+x\\sum_{k=0}^{n-\(i+1\)}a_{k+i+1}x^k=a_ix^0+\\sum_{k=0}^{n-i-1}a_{k+i+1}x^{k+1}=\\sum_{k=-1}^{n-i-1}a_{k+i+1}x^{k+1}=\\sum_{k=0}^{n-i}a_{k+i}x^k)

**Termination:**At the end of the cycle i = -1, Will i = 0 Substitution
![](http://latex.codecogs.com/gif.latex?y=sum_{k=0}^{n}a_{k}x^k)

**d.**
Earlier has proved that the cycle is unchanged, and the conclusion is naturally established.


### Problems 4 : Inversions
***
Let A[1..n] be an array of n distinct numbers. If i < j and A[i] > A[j], then the pair (i, j) is called an inversion of A.

a. List the five inversions of the array 2, 3, 8, 6, 1.

b. What array with elements from the set {1, 2, . . . , n} has the most inversions? How
many does it have?

c. What is the relationship between the running time of insertion sort and the number of
inversions in the input array? Justify your answer.

d. Give an algorithm that determines the number of inversions in any permutation on n
elements in Θ(n lg n) worst-case time. (Hint: Modify merge sort.)

### `Answer`
**a.**
(1, 5), (2, 5), (3, 5), (4, 5), (3, 4)

**b.** The array with decending order arrangement i.e. {n, n-1, n-2, ..., 3, 2, 1} has the most inversions.  
Number of inversions = Number of ways to choose two distinct element from the above set = n(n-1)/2.  

**c.** we know that the inner while loop of insertion sort shift the elements to left to their right position. So if there is more inversion in an array, then we need to shift more elements. Hence as the number of inversions increases, running time of insertion sort increases.

**d.**

[PythonCode](./exercise_code/inversions.py)

[CppCode](./exercise_code/inversions.cpp)

***
Follow [@louis1992](https://github.com/gzc) on github to help finish this task.


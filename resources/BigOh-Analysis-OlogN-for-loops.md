# Big-Oh Analysis: Simple O(logN) for-loops

With a simple for-loop there are two variables that influence the number of times the loop iterates. The first is obviously the size of your input (n) and the second is the size of your iterator. I like to think of n as your stopping point and the iterator as your “step” value. Let’s play around with some examples:

    for(int i=0; i<n; i++)

That’s the foundation for all of our for-loops. It’s pretty clear that we will iterate through the loop n number of times, that is we stop at n, and our step size is 1.

The next loop to consider is:

    for(int i=0; i<n*n; i++)

With this loop we are still incrementing the iterator by one, however our stop value is now much larger, so we will have to iterate through the loop many more times (n^2 to be precise).

For the next example, let’s return our stop value back to n, but let experiment with our step value:

    for(int i=0; i<n; i+2)

Now instead of stepping through the length of n in steps of 1, we are stepping through in steps of 2. Here is a table of the values of i:


| Iterations | i  |
|------------|----|
| 1          | 2  |
| 2          | 4  |
| 3          | 6  |
| 4          | 8  |
| 5          | 19 |

As you can see after the 5th iteration we are taking steps of size 10. In the above example, n=10, i.e. we stop when we hit 10, we’d stop after 5 iterations, which happens to be n/2. If our increment step was i+3, we’d have multiples of 3, and the number of times the loop would iterate through would be n/3, because division “undoes” multiplication. 

Finally, lets take a look at a slightly more complex example:

    for(int i=0; i<n; i*2)

Here we aren’t adding two each iteration, we are multiply by two so our table of values looks like this:

| Iterations | i = i*2          |
|------------|------------------|
| 1          | 1*2 = 2 = 2^1    |
| 2          | 2*2 = 4 = 2^2    |
| 3          | 4*2 = 8 = 2^3    |
| 4          | 8*2 = 16 = 2^4   |
| 5          | 16*2 = 32 = 2^5  |

You can see the iterator, or steps, are growing exponentially (powers of 2). What we now have to think about is how quickly we approach our stopping point.

If n=10 we’d hit it during our 3rd iteration, if n=50 we’d hit it on our 5th iteration, if n=100, we’d hit it on our 6th iteration.

| n           | Iterations |
|-------------|------------|
| 10          | 3          |
| 100         | 6          |
| 1,000       | 9          |
| 10,000      | 13         |
| 100,000     | 16         |
| 1,000,000   | 19         |
| 10,000,000  | 23         |
| 100,000,000 | 15         |

We could graph this relationship as follows:

![O(logN)](http://i.imgur.com/CgUBeDI.png)

From here it should start to be clear that we are working with a logarithmic time complexity. Just think of it this way, with the example of i=i+2, each iteration, we had multiples of 2, and to determine the runtime we essentially divided n by 2 to determine the number of iterations because division is the opposite of multiplication. In this situation we are dealing with exponential growth, and the opposite of exponential growth is logarithmic growth. 

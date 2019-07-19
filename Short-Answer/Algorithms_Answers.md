Add your answers to the Algorithms exercises here.

# Exercise I

```
a)  a = 0                                       # O(1)
    while (a < n * n * n):                      # O(n^3)
      a = a + n * n                             # O(1)
```

a) Overall complexity as it is: O(1) + O(n^3) \* O(1) => **O(n^3)**. Still, at most
cases in the default (binary) arithmetic, the line `a = a + n * n` allows to
reduce the complexity to the `linear` because for the given value of `n` this
while loop is going to execute `n` times. The final time complexity is **O(n)**.

```
b)  sum = 0 // 0(1)
    for i in range(n):                          # 0(n) * 0(n^3) = 0(^4)
      i += 1                                    # 0(1)
      for j in range(i + 1, n):                 # 0(n) * 0(n^2) = 0(^3)
        j += 1                                  # 0(1)
        for k in range(j + 1, n):               # 0(n) * 0(n) = 0(^2)
          k += 1                                # 0(1)
          for l in range(k + 1, 10 + k):        # 0(n) * 0(n) = 0(^n)
            sum += 1                            # 0(1)
```

b) Our outermost loop has runtime complexity O(n). The next two loops down also have runtime complexity O(n) if we drop the constants in each range. The final loop should also have runtime complexity O(n) because k is being derived from a loop that iterates n times. This suggests that our algorithm has overall complexity of O(n^4).

```
c)  def bunnyEars(bunnies):
      if bunnies == 0:                          # O(1)
        return 0                                # O(1)

      return 2 + bunnyEars(bunnies-1)           # O(n)
```

c.) This runtime is O(N). What happens is that for each n we add to the bunnies function, we add another call to the stack. I.e. for n = 5, we cann bunnyEars 5 times, so there's a direct relation between our Big 0 and the size of our call stack, which determines our runtime.

Exercise II

This is a perfect opportunity to use a binary search. Since floors are ordered in ascending order, we already have a sorted list of values to work off of. So what we should do is choose the midpoint and see if the egg breaks or doesnt break when tossed from that floor, if it doesn't break then we divide the remaining rooms above us in half and move to that point. If it does break, then we move to the midpoint of the rooms below us. We then repeat this process until we find the exact highest floor you can drop an egg from so that it doesn't break.

The runtime of this algo is O(log N). Which means that if we moved from 32 -> 64 floors, it would only take 1 extra move to find the exact floor.

# Parallel, Concurrent and Distributed programming in Java

These are my solutions to these three courses. Below I added short comments to
each week so that I remember better what it's about and that you, the reader,
could have a better idea too.

## Parallel programming in Java

### Week 0

Preparation week. The purpose is to test your environment. No actual task to do.

### Week 1 ForkJoin

In this week we need to calculate reciprocal array sum. We're using Java's
ForkJoin framework to parallelize our calculations. There are different ways to
interact with the ForkJoin framework, and in this week we're extending
`RecursiveAction` and overriding `compute()` method. In `compute()` method we
determine current size of the current range of the that we need to process. If
it's small enough, we are processing it immediately. Otherwise, we divide it
into two parts (left and right) and process them recursively.

The minimal threshold value determines how many ForJoin tasks we will totally
create. Notice that I didn't manage to pass the tests locally and I didn't
submit the solution to the Coursera grader. Many students reported the same
problem on the forums. Still, there was a significant improvement over the
linear execution, just not as big as expected by the creators of the homework.

### Week 2 Streams

This week we're using Java Streams API to build a pipeline that computes some
student analytics. Nothing difficult here, you just need to understand which
data type you have at each pipeline stage and convert data types accordingly if
needed.

### Week 3 PCDP

This week we are learning how to use PCDP library (a library developed to teach
parallel computations) to parallelize matrix multiplications. Again, the task is
trivial as you only need to replace one method name with another.

### Week 4 Fuzzy phasers

In this week we explore the functionality of fuzzy phasers. The idea is that if
we have an array which average sum we need to compute, we can split work into
`N` tasks and do it concurrently. The improvement is that a task `i` only has to
for for tasks `i-1` and `i+1` to complete. To achieve that, we use `N` phasers
and we call their methods `arrive()` and `awaitAdvance(int phase)`. Notice here
since we run multiple iterations over the same array, this `phase` number keeps
growing and it's crucially important to keep track of the current phase.

``` text
    1 2 3
     \ /
    1 2 3
```

This illustrates that task 2 depends on completion of tasks 1 and 3.

## Concurrent programming in Java

### Week 1 Locks

In this week we were introduced to locks, the basic primitive for
synchronization. Java's `synchronized` keyword is pretty much the same lock that
guards the whole method. Lock, however, can be made more granular. In this week
we applied `ReadWrite` lock to benefit from the fact that read only methods can
have concurrent access to the data, while read-and-write methods should be
guarded by a lock.

### Week 2 Isolation

This week we are introduced to the concepts of critical sections, atomic
variables and isolation. Being a more high-level synchronization construct,
isolation allows for simpler semantics providing the same or even better level
of efficiency. To make things faster in the homework, we use PCDP library and
object-level isolation, not global isolation.

### Week 3 Actors

This week we are introduced to the concept of actors. To explain it in my own
words, actors are independent units of computation that you can communicate with
using `send` method. In the miniproject we need to implement the famous Sieve of
Eratosthenes using actors. To do that, we create a chain of actors that
one-by-one check whether a given number is divisible by the range of numbers,
assigned to the given actor. To make it more efficient, a single actor is
assigned a bunch of numbers, e.g. 1000, not just one.

### Week 4

## Distributed programming in Java

### Week 1

### Week 2

### Week 3

### Week 4

## Author

2017-2018, Yuri Bochkarev

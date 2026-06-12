---
title: "Timing applications"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by siddartha on 2007-12-07
Hello,

How can I time an application for the time it takes to completely load and for doing certain operations? Besides the classical with holding a timer in the right hand and click when the process starts and when it ends.

Cheers,
Sidd

---

### Post by Hospadar on 2007-12-07
unless you are writing the application yourself, I don't think there is a general solution.  All programs use all different interfaces and you'd probably have to write some custom software to track progress and load times and whatnot.  I'd bet at least you could find some timers that run on the machine with maybe some key shortcuts to help get a better time than a stopwatch

If you are looking to benchmark a system, there are applications that will do that, if you google "linux benchmarking" you can find all sorts of stuff.

---

### Post by SOULRiDER on 2007-12-07
Just use time :P

It starts counting whent he process starts and stops once its finished. It then displays the total time. For example you could time how long it takes to update package lists.
```
time sudo aptitude update
```

---

### Post by siddartha on 2007-12-07
I was thinking of something like How fast does Open Office load in comparison with the time it takes to load an empty document in Abiword and in KWrite. Or how long it takes to load this 500 page book in all three. Or how fast it can either of them reformat the whole text.

---


---
title: "Analyzing bootchart graph"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by kag on 2007-10-03
I installed bootchart and I have the generated PNG, but I'm not sure how to interpret it.

Can someone explain to me how to read it?

---

### Post by Paulmd on 2007-10-04
> **kag said:**
> I installed bootchart and I have the generated PNG, but I'm not sure how to interpret it.

Can someone explain to me how to read it?

The top graph shows %CPU usage and time waiting for I/O. 


The lower portion is pretty simple, it shows start and stop times of various processes. The colors within the bars indicate whether the process is idling, using CPU or waiting for I/O.

---

### Post by kag on 2007-10-09
Yes, but how can I figure out which processes are taking longer than they should?

---

### Post by Paulmd on 2007-10-09
> **kag said:**
> Yes, but how can I figure out which processes are taking longer than they should?


You can't, really, without a baseline or benchmark to compare against.

You might use it as a tool to figure out which process are taking the longest, and then look up what they do, and whether or not you need them to run.

---


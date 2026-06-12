---
title: "A random networking quesion"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Rij on 2007-09-27
I am doing some prelim experiments in which I want to compare the latency of two data forwarding techniques over a network. I want to use a very simplistic view of the system. For example, no congestion etc. Essentially, latency = delay at each of the intermediate nodes + delay in traversing the intermediate links. Now delay at the nodes depend upon numerous factors. But I just want an approach where delay is proportional to the number of pkts waiting to be processed at the node. I am using a FIFO/drop tail policy. Is there any kind of characterization that is available from previous research that I might be able to use? All I really want is a formula:
Delay = f(Q occupany).

Any pointers, including a better forum to ask this question, will be greatly appreciated. Again, the key is that I want to make a qualitative comparison and accurate realistic delay numbers are not important.

---

### Post by Rij on 2007-09-27
Ok, I am modifying my question a bit. I assume a M/E10/1 model. What is the queueing delay for this and what are the sensible values for the parameters?

---

### Post by dwhitney67 on 2007-09-27
I think you are on the wrong forum.  This is the Ubuntu Forum.  Not the "Do my homework" Forum.

---


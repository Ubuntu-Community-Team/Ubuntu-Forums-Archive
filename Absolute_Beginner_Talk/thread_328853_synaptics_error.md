---
title: "synaptics error"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2006-12-31
E: Malformed line 26 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

How do I correct the error? Cannot open synaptics at all

---

### Post by an.echte.trilingue on 2006-12-31
A parsing error means that you messed up the syntax in a config file, in this case /etc/apt/sources.list.  That can happen if you click on the wrong thing in synaptic; it is not perfect yet.  Please post the file /etc/apt/sources.list so that we can find the error and fix it.

Take care,
-mat

---

### Post by smoker on 2006-12-31
not sure what the errors mean, though i think your sources list is damaged in some way.

there is info here, and replacement lists to copy and paste, that may help if you think so,

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

hope this helps

---

### Post by an.echte.trilingue on 2006-12-31
> **smoker said:**
> not sure what the errors mean, though i think your sources list is damaged in some way.

there is info here, and replacement lists to copy and paste, that may help if you think so,

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

hope this helps

I would not recommend this because it does not use the mirrors that the installer's sources.list uses, so if the OP is not near the server, this can cause slowdown for downloads and in general it puts more load on the internet.  Besides, the OP might not want all the non-free stuff.

A parsing error is an easy fix, usually only being a missing word, if the OP will post his/her sources.list.  Of course, it is up to the OP do do what s/he wants.

Take care
-mat

---

### Post by sailor2001 on 2006-12-31
that did it, thanks.........keep cool

---


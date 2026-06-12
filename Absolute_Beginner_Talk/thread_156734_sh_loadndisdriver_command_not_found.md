---
title: "sh: loadndisdriver: command not found"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by benfinkel on 2006-04-07
Well,

I'm continuing to try and get ndiswrapper going... no luck.

When I run 

sudo modprobe ndiswrapper

I get the following response:

sh: loadndisdriver: command not found


Any ideas?

Thanks again!

---

### Post by benfinkel on 2006-04-07
I should fill you all in.


I've downloaded ndiswrapper-source and ndiswrapper-utils from Synaptic.

I had to type sudo depmod -a before I could even get modprobe ndiswrapper to recognize anything.

---


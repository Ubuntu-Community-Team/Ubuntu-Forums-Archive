---
title: "synaptic programs installed export"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2006-11-19
So I have a computer set up exactly how I want it and I want to install ubuntu on another is there a way I can export the list of and/or a script to install the same programs on the next computer?  I have used the aptoncd for things which I had to go around synaptic to get and it works great actually, but for the synaptic downloaded programs I have no idea how to transfer them.  Other than one at a time.  Even print a list of them for reference would help.

---

### Post by aysiu on 2006-11-19
> **Rush_898 said:**
> So I have a computer set up exactly how I want it and I want to install ubuntu on another is there a way I can export the list of and/or a script to install the same programs on the next computer?  I have used the aptoncd for things which I had to go around synaptic to get and it works great actually, but for the synaptic downloaded programs I have no idea how to transfer them.  Other than one at a time.  Even print a list of them for reference would help.
There's probably a way to do this by plopping your list of programs into a text file and using that ```
dpkg -l > installedprograms.txt
``` But you can also just clone your current installation with [this tutorial](http://www.psychocats.net/ubuntu/partimage).

---


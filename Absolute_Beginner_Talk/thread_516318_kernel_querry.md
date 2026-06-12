---
title: "kernel querry"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by rasesh_raz on 2007-08-03
hey do we need to download the patches as well for kernel compilation  
sudo apt-get install build-essential bin86 kernel-package
 this right now
this is giving error that cannot find find bin86

---

### Post by Alterax on 2007-08-03
I've never had to; I just usually download build-essential, a couple of other things (automake, et cetera) and the source code:

sudo apt-get install linux-source-`uname -r`

The uname -r bit returns the version of the kernel you are using so you can get the newer source.  You can also get it from Kernel.org, but I seldom find anything new that I just can't live without.  In fact, since I switched to Feisty, I can't think of any real reason I need a custom kernel now...

--Alterax

---


---
title: "Please help with VGA card"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by emar82 on 2006-10-04
Hello everyone, I just built my new machine and am running ubuntu64 on it. My VGA card is nothing expensive but I would like to get direct rendering turned on. I have a MSI NX6200TC NVIDIA GeForce. How can I go about setting this up? In terminal glxinfo returns the following

name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None

---

### Post by bodhi.zazen on 2006-10-04
Try these two links:

[[color=blue]bodhi's resolution solution[/color]](http://ubuntuforums.org/showthread.php?p=1566609#post1566609)

[Ubuntu documentation how to fix video resolution](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by emar82 on 2006-10-04
Hi, thanks for the reply. Quick question, is that just for problems with screen resolutions? Because that is fine.

---

### Post by bodhi.zazen on 2006-10-04
> **emar82 said:**
> Hi, thanks for the reply. Quick question, is that just for problems with screen resolutions? Because that is fine.

No, it covers the nvidia driver, primarily via a link, but with some advice on what has worked in the past.

You should find it at least helpful as you embark.....

---

### Post by emar82 on 2006-10-04
That worked perfectly :) Thanks a ton!

---


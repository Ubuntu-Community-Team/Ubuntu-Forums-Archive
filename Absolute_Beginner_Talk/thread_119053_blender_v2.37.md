---
title: "blender v2.37"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by jade on 2006-01-18
I've switched to breezy and found blender 2.37 doesn't start and halts with this line

"/usr/bin/blender: line 46:  8164 Illegal instruction     blender-bin $@"

could use some guidance from anyone with more experience

---

### Post by jade on 2006-01-18
Okay I upgraded all the updates and now when I run the comman blender I getall of this extra stuff

Using Python version 2.4
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
/usr/bin/blender: line 46:  7528 Segmentation fault      blender-bin $@

Do I track down and change settings for my graphics card or can I use options with the blender command? Or maybe something completely different.

---

### Post by jade on 2006-01-19
Hey, I was thinking blender worked just dandy in hoary. So I found the version 2.36 for horary and did the dpkg thing discovered I had to synaptic ilbstd++5 or something and wouldn't you know it works just dandy again. Thanks, to all you who helped me, ever so much.
jade a.k.a. blue42

---


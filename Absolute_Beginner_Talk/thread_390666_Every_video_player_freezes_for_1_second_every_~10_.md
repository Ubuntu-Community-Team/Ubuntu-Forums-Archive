---
title: "Every video player freezes for 1 second every ~10 second... Why?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by ksamvel on 2007-03-22
Hi,

I have installed a bunch of Video players with all codecs. Every movie is played but with systematic freezes for ~1 second. It happens approximately every 10 seconds. This is extremely annoying and unpleasant side effect while watching movies.

Guys help... Any ideas?

---

### Post by justleen on 2007-03-22
do you have the correct drivers for your video card installed?
if i play a movie on an out-of-the-box install, i cant play any videos either..
After installing the nvidia drivers, everything works just fine.

---

### Post by AndrewBarber on 2007-03-22
For help installing graphics cards take a look at [this wiki page](https://help.ubuntu.com/community/BinaryDriverHowto).

Otherwise.. Is the system on a laptop? Mine doesn't show videos too great when running on battery.

---

### Post by ksamvel on 2007-03-22
My KUbuntu installation lives in my Laptop. But I have never thought about any Video Card drivers. Every graphics worked in Ubuntu automatically from the very beginning.

---

### Post by AndrewBarber on 2007-03-22
Try
```

glxinfo |grep direct

```
If it returns a no then you may be better to get the driver installed :)

---

### Post by ksamvel on 2007-03-22
Here is an output I got:

```
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
```

It says: YES. So, do I still need to worry about driver or the problem is in something else?

---

### Post by AndrewBarber on 2007-03-23
I would maybe say it was something else then.

Is the meda ok?

Alot of people have found the VLC is the best choice.. have you tried that?

---


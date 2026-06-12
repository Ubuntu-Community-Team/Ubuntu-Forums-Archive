---
title: "[SOLVED] How much ram is in this beast"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-07-31
is there a command to tell how much ram is installed through the terminal or similar?

---

### Post by DBStevens on 2007-07-31
free

---

### Post by aysiu on 2007-07-31
```
top
``` works, too. Press *q* to quit when you're done viewing.

---

### Post by Ripfox on 2007-07-31
Nice...you learn something new every day. 

Thanks.

---

### Post by Inxsible on 2007-08-01
There seems to be a discrepancy in my memory readings

The CPU monitor screenlet that I have shows Memory used 450 MB. The gnome system monitor also shows 450 MB used, but top and free below show different numbers. Am I reading it wrong?

Seems like the free and used memory are reversed in the commands free and top :(

```
inxsible@HPdv9000t:~$ free
             total       used       free     shared    buffers     cached
Mem:       2074556    1580504     494052          0     426196     684896
-/+ buffers/cache:     469412    1605144
Swap:      1004020          0    1004020
``````
inxsible@HPdv9000t:~$ top

top - 00:12:33 up 1 day,  5:27,  2 users,  load average: 0.19, 0.13, 0.13
Tasks: 131 total,   1 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3%us,  1.5%sy,  0.0%ni, 95.0%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2074556k total,  1579820k used,   494736k free,   426328k buffers
Swap:  1004020k total,        0k used,  1004020k free,   684952k cached
```

---

### Post by aninaiian on 2007-08-01
Subtract cache and buffer from used...

---

### Post by MetalMusicAddict on 2007-08-01
**free -m** will show it in MBs.

---

### Post by Inxsible on 2007-08-01
> **aninaiian said:**
> Subtract cache and buffer from used...
thanks

feeling pretty stupid now #-o

---

### Post by Ripfox on 2007-08-01
Ok this is weirding me out now...it says this machine has 749 mb and only 38mb free!

What the hell is using all that memory??

---

### Post by DBStevens on 2007-08-01
Probably the 100 or tasks that are running on your machine, and the space used as filesystem cache for what ever you have played with since the machine was booted.

---

### Post by Ripfox on 2007-08-01
err...that doesn't seem right.

---

### Post by DBStevens on 2007-08-01
But it is.

This question gets asks on a regular basis, unless there is a memory leak in your system my answer is correct.

Linux doesn't free memory until it has to.   It  keeps cached filesystem information so it doesn''t have to keep getting it over and over.

---

### Post by DBStevens on 2007-08-01
top - 21:12:32 up 19 min,  3 users,  load average: 0.81, 0.78, 0.51
Tasks: 102 total,   3 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s): 33.3%us,  0.3%sy,  0.0%ni, 66.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1035004k total,   467440k used,   567564k free,    16352k buffers
Swap:  3104760k total,        0k used,  3104760k free,   301644k cached

From my system which has 1 mozilla window open, two terminal sessions, tv, and thunderbird,  Gnome is the window manager, and there are 6 Apache sessions.

---

### Post by Ripfox on 2007-08-02
OH I see...very interesting. So it's not actually being USED, just at the ready.

---

### Post by DBStevens on 2007-08-02
Well it is being used just not always for what you are doing at the moment ;-).

There is a downside to this in certain cases, for those cases one has to make adjustments.

---


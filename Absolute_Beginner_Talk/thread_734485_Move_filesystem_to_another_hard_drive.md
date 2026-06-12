---
title: "Move filesystem to another hard drive"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by sparkguitar05 on 2008-03-24
I searched for this in the forums but all the explanations were too confusing and general.  What I want is a good step-by-step guide....

What I want to do is move my root filesystem (/) to another hard drive.

Here is my current setup:
---INTERNAL IDE DRIVE---
> 
/dev/sda1              63       64259       32098+   6  FAT16   (stuff Dell put on my computer)
/dev/sda2   *       64260   304415684   152175712+   7  HPFS/NTFS   (Windows XP for dual boot)
/dev/sda3       304624530   312496379     3935925   db  CP/M / CTOS / ...    (more crap from Dell)
/dev/sda4       304415685   304624529      104422+  83  Linux    (/boot)


---EXTERNAL USB DRIVE---
> 
/dev/sdh1              63   436405724   218202831    7  HPFS/NTFS   (some extra storage)
/dev/sdh2       436405725   478351439    20972857+  83  Linux   (/) (this is what i want to move)
/dev/sdh3       478351440   620944379    71296470   83  Linux    (/home)
/dev/sdh4       620944380   625137344     2096482+  82  Linux swap / Solaris  (swap)


All I want to do is move the '/' to my internal drive, but keep the '/home' on the external drive.  Please be very detailed if I have to do anything in the terminal, cause I'm a total noob.

---

### Post by garyed on 2008-03-24
I think the "dd" command would be a good option for what you're trying to do.
I'm a little new at this so I'm nervous to give you the code in case I make a mistake.
It's a very dangerous command if used wrong so I would do a little homework before using it.
It can copy an image of your partition.  The basic command is: 
dd  if=(file or device to be copied)  of=(file device to be copied to)
Do a little research & I'm sure you'll find the exact code for what you want to do.

---


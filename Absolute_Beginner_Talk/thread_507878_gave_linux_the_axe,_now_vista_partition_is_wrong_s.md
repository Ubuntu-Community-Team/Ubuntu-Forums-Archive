---
title: "gave linux the axe, now vista partition is wrong size"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by kefurd06 on 2007-07-23
i used gparted to remove my linux and swap partitions, and resize my vista partition to use the whole drive, but in vista i don't have the new free space. i've ran error checking on the drive (computer > c > properties > tools > error-checking) once in safe mode and once on bootup, and it still doesn't show the right size. what do i do?

---

### Post by JustAboutRealJAR on 2007-07-23
try booting linux from the install CD and running gparted again.

see if it also see's the partition as the wrong size. If so maybe it encountered and error and didn't tell you, or you forgot to hit apply or something like that.

if gparted says the partition is the size it should be then you should probably try another partitioning program. I don't know any off hand... just search google.

---

### Post by jimbob on 2007-07-23
I don't have Vista but from what I have read you should have probably used the Vista tools to do the resize.  See if it will let you do it now.

Sorry you are leaving - was it something we said?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by ReaderRat on 2007-07-23
Just a guess, but I should think that if you resized Vista to include the Ubuntu patition space, you would have a space that you could not use - the space would not be NTFS formatted.

A downer, but I would suggest re-installing Vista from scratch (after you use gparted to clear all partitions.

---


---
title: "Making an Image of a Floppy Disk"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by Bl0wn2b1ts on 2005-07-06
Hi,

Is there a program that anyone knows of that does the same thing as for example winimage ??

I would like to be able to create images of floppy disk

thanks in advance

---

### Post by AntiDragon on 2005-07-06
Hi.

I believe you can use the **dd** command to make images.

Use **man dd** for more details, but to copy a disk to an image:

[FONT=Courier New]dd  if=/dev/fd0  of=[filename][/FONT]

and the reverse:

[FONT=Courier New]dd if=[floppy-image]  of=/dev/fd0[/FONT]

And all thanks to the wonders of Linux block devices!  :grin: 

Check out [this site](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html) as well.

---


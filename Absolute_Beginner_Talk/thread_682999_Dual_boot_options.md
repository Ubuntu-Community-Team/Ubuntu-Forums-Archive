---
title: "Dual boot options"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by sheki1 on 2008-01-30
Hello, I recently added an Ubuntu partition/install on my Vista notebook.

When I boot the system I get the following options:

Ubuntu 7.10 kernel 2.6.22-14-generic
Ubuntu 7.10 kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10 kernel 2.6.22-14-generic memtest86+
Windows loader
Windows loader

What's the second and third Ubuntu choices as well as the second Windows option for?

Thanks!

---

### Post by jan quark on 2008-01-30
the recovery mode lets you login in text base mode to rescue your system 
the memtest86+ is an advanced memory diagnostic tool
[http://www.memtest.org/](http://www.memtest.org/)

why you have two windows loaders, no idea

---

### Post by Atomic Dog on 2008-01-30
Maybe the second partition is a recovery partition.  I have noticed some manufactures squeak in a 10 gig partition with vista setup files in case recovery is needed.

---

### Post by Rocket2DMn on 2008-01-30
I've never seen a dual boot for vista with my own eyes, but I would speculate that the second windows loader is some sort of recovery mode for vista (if it's even supposed to be there).  What happens when you boot into both of them?
Any dual booting vista users out there who can enlighten us?

---

### Post by sheki1 on 2008-01-30
I've only chosen the first Windows option as I didn't/don't know what the second one was for.  Next time i reboot I'll chose the second...

---

### Post by sheki1 on 2008-01-31
I'm sure folks will think this taboo, but how do I change the startup BOOT option from Ubuntu to Vista?

---

### Post by seventhc on 2008-01-31
I did a dual boot with vista for a very short time, and this is not how it looked. I also had a recovery partition, but that didn't show in the boot options. That may be different with each machine as mine if you want to recover using the partition you still initialize it by booting to the vista cd. From there you can choose recover or full reinstall. I removed vista and that partition and to test it I did a full reinstall of vista and it actually recreates that partition. But my boot options read as Windows Vista, or something along those lines, no boot loader.

---

### Post by OldGrey on 2008-01-31
"I'm sure folks will think this taboo, but how do I change the startup BOOT option from Ubuntu to Vista?"


Its been asked lots of times, a quick search will find you the answer

---

### Post by seventhc on 2008-01-31
> **sheki1 said:**
> I'm sure folks will think this taboo, but how do I change the startup BOOT option from Ubuntu to Vista?

```
sudo gedit /boot/grub/menu.lst
```change the name from bootloader to vista or whatever you want.
It's a good idea to make a back up copy before you change anything. ;)
changing names is completely safe, but if you delete something by mistake without knowing it, you'll have a backup. :)

---

### Post by jaytek13 on 2008-01-31
> **sheki1 said:**
> I'm sure folks will think this taboo, but how do I change the startup BOOT option from Ubuntu to Vista?



To do this you have to edit the menu.lst file (lst is lower case L)

```

sudo gedit /boot/grub/menu.lst

```

At the top of the file you should see something that says "default 0"

At the bottom of the file you will see some entries for the various OS options.

You have to change "default 0" to the corresponding Windows option. These options start at 0, so the 1st OS it lists is 0, while the 3rd is 2, the 5th is 4, etc. So you just change "default 0" to whatever windows option you need. 

While your in there you can also give yourself some more time to select the options if you need to. The default is 3 seconds. You'd just change the "timeout 3" option to however many seconds you need.

---

### Post by seventhc on 2008-01-31
oops, i misunderstood, I thought you were wanting to change the name. #-o

---


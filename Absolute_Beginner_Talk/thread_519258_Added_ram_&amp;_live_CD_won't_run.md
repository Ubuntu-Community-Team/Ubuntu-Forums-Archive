---
title: "Added ram &amp; live CD won't run"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by reabralop on 2007-08-06
Hello.
I have run the live disk on this machine before but it doesn't seem to work now. The only change that I know off is installing 2 more gigs of ram to give me a total of 4 gb. The disk is the 64 bit 7.04 version and I don't know if the ram is causing it or not.

After I select the install/ run live it begins the process for running but eventually the screen & the hd light go blank. As I mentioned I've run the disk before the ram upgrade just fine. Does anyone know what may cause this? Thank you.

---

### Post by bodhi.zazen on 2007-08-06
Probably the ram

boot the CD

When you get to the grub menu, type e to edit the boot line

Add mem=2048m to the kernel line

see if it boots (this will boot your system with 2 Gb ram)

If that works, take a look at the server kernel, I think that will handle your higher ram

---

### Post by insane_alien on 2007-08-06
try running a memtest. 

it'll tell you if it is the RAM. also, check the CD for defects.

you can also try reseating the RAM it might be slightly off. it happens sometimes.

---

### Post by Rocket2DMn on 2007-08-06
> **bodhi.zazen said:**
> Add mem=2024m to the kernel line
see if it boots (this will boot your system with 2 Gb ram)

Don't quote me on this, but shouldn't it be 2048 since 1 GB is 1024?

---

### Post by bodhi.zazen on 2007-08-06
> **Rocket2DMn said:**
> Don't quote me on this, but shouldn't it be 2048 since 1 GB is 1024?

OK, I fixed it, thx

---

### Post by reabralop on 2007-08-06
That did it. I'm running the disk now. I'm almost positive the ram is good because the bios reads all of it, I removed the original 2 sticks, and swapped slots and it works (in windows) on all accounts. 

What did you mean by resetting the ram, ie how?

---

### Post by bodhi.zazen on 2007-08-06
I do not know how to solve the problem but it seems for some reason the 64 bit kernel can not handle the high RAM.

You can post in the 64 bit forum or try the server kernel (you would need to install to hard drive, then install the server kernel, and finally boot the server kernel which may well be 32 bit).

[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---


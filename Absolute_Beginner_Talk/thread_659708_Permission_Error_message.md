---
title: "Permission Error message"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Luckyjinxes on 2008-01-06
I am new to Linux and am trying to launch it for the first time.  I installed the i386 livecd but now after it finished loading it will run the process then several permission denied messages will come up.  What can i do?

---

### Post by mattismyname on 2008-01-06
Can you give more details?  Which CD did you install?  Did you actually install the OS or did you just load the CD.  The more details you can give, the better.  :)

---

### Post by PeterJS on 2008-01-06
> **mattismyname said:**
> Can you give more details?  Which CD did you install?  Did you actually install the OS or did you just load the CD.  The more details you can give, the better.  :)

Another big question is what are you trying to do?

---

### Post by Luckyjinxes on 2008-01-06
Sorry!  im new at all this.  its the 7.10 i386 version.  I wanted to try it out before installing it by "live cd"?  So i downloaded it off the site and burned the iso image to a disc.  i jus want to load the CD so i can experience it before i decide to switch from XP if i choose to do so

---

### Post by mattismyname on 2008-01-06
When you boot from the CD is it just a bunch of white text on a black background or do you see a brown "desktop" with menus and such?

---

### Post by Luckyjinxes on 2008-01-06
yeh i see the unbuntu logo and the options

---

### Post by PeterJS on 2008-01-06
I've been working with Lucky on AIM. So far we've tried re-burning at 16x, and that didn't clear things up any. Here's a video of it booting up:
[Ubuntu Boot up](http://oregonstate.edu/~sandinp/Ubuntu_boot_error.mp4)
Any idea guys?

---

### Post by ajmorris on 2008-01-06
Hi there, can you give us an overview of the Specifications of your PC, i.e your CPU, motherboard, etc.

---

### Post by Luckyjinxes on 2008-01-06
Yes thanks for your help.  Specs can be found here [http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=463521&os=228&lang=en&cc=us&docname=c00313194](http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=463521&os=228&lang=en&cc=us&docname=c00313194).  everything is the same except that my pc runs 1gb of ram and i have a nvidia geforce 8600 vid card

---

### Post by mattismyname on 2008-01-06
Good video.  Can you use <shift>+<pgup> to scroll up so we can see the other errors coming out on the screen?

ajmorris:  It's some sort of HP machine

---

### Post by PeterJS on 2008-01-06
Tried booting up a knoppix CD to see if it was something ubuntu specific. That didn't go much better it got as far as locating the cdrom device to mount the root file system from, and failed. From the busybox fall back shell I had Lucky run ls /dev/hd* and /dev/scd* to try and find the device nodes manually. Neither of those turned up anything.

The prevailing theory I have is that the permission denied errors from ubuntu are from the non-existent cdrom device node. Any idea if this is the right direction, or where to go from here.

---

### Post by Luckyjinxes on 2008-01-06
> **mattismyname said:**
> Good video.  Can you use <shift>+<pgup> to scroll up so we can see the other errors coming out on the screen?

I tried but i cant?  Sorry

---

### Post by ajmorris on 2008-01-06
are the live cds 64bit versions? I mean, i cant boot 32bit live cds on my 64bit box.

---

### Post by rkd on 2008-01-06
ajmorris: That's odd. I can boot 32-bit versions on my Athlon 64 without trouble. I wonder what causes the difference and whether it has any bearing on Luckyjinxes' problem.

---

### Post by Luckyjinxes on 2008-01-06
> **ajmorris said:**
> are the live cds 64bit versions? I mean, i cant boot 32bit live cds on my 64bit box.

It is the i386 version, but i also tried the 64bit version.  the 64bit version couldnt even get me to the load screen lol

---

### Post by ajmorris on 2008-01-06
> **Luckyjinxes said:**
> It is the i386 version, but i also tried the 64bit version.  the 64bit version couldnt even get me to the load screen lol

That is quite odd. When you say > **Luckyjinxes said:**
>  couldnt even get me to the load screen do you mean it wouldnt get to the screen where you choose to boot of the CD (as in there is an ubuntu logo above lots of options)? or you chose to boot the CD, but the boot screen wouldnt show? (the screen with ubuntu above it, with the loading bar below.

---

### Post by ajmorris on 2008-01-06
> **rkd said:**
> ajmorris: That's odd. I can boot 32-bit versions on my Athlon 64 without trouble. I wonder what causes the difference and whether it has any bearing on Luckyjinxes' problem.


Yeah, 64bit hardware is supposed to be fully backward compatible, however, i can just not boot off 32bit live-cds. And i've never bothered to pursue it, because i dont need the 32bit live-cds, but there must be some sort of fix for it. But Lucky's problem seems to be quite unique, googling doesnt reveal very much at all, so this is going to be very hard to solve.

---

### Post by philinux on 2008-01-06
forgive me if I'm off track but the video shows you choosing option 2 safe graphics mode.

Why not choose option one. It does not install just runs the live cd.

---

### Post by Luckyjinxes on 2008-01-06
> **philinux said:**
> forgive me if I'm off track but the video shows you choosing option 2 safe graphics mode.

Why not choose option one. It does not install just runs the live cd.

No i just did that to show that im active.  I did select option 1 thought, start/install.

---

### Post by Luckyjinxes on 2008-01-06
> **ajmorris said:**
> That is quite odd. When you say  do you mean it wouldnt get to the screen where you choose to boot of the CD (as in there is an ubuntu logo above lots of options)? or you chose to boot the CD, but the boot screen wouldnt show? (the screen with ubuntu above it, with the loading bar below.

Please check the video, it loads but i cant get to desktop.  The video is on page 1 posted by another user im not sure his name though

---

### Post by ajmorris on 2008-01-06
> **Luckyjinxes said:**
> Please check the video, it loads but i cant get to desktop.  The video is on page 1 posted by another user im not sure his name though

is that video of the i386 or the 64bit though?

 I was talking about the 64bit

---

### Post by Luckyjinxes on 2008-01-06
its the i386 version.  The 64bit version wont even load after selecting start/install

---


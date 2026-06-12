---
title: "the boot time of 7.10 is more longer than 7.04"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by helai on 2007-10-21
I just upgrade my ubuntu from 7.04 to 7.1,but i'm frustrated with the longer boot up time than 7.04,all the comparision is baseon on the first installaion and not optimization,of course I haven't record the time,only by my feeling
just like when i heared the login in sound ,then in 7.04,the screen of  gnome will be appeared at the same time,but in gusty ,it still need seconds

any advices are welcome

---

### Post by catfacts on 2007-10-21
Do you have a lot of stuff installed, special scrips that run on startup, what do you run, ie 1gig ram 100gig HD, Check to see if your comp is up to spec. Also are you runing special login managers that may slow this down?

---

### Post by arron on 2007-10-22
I got the same thing.... 7.04 after 6 months of running, and all my stuff installed startup from grub enter to login prompt 42 seconds.  7.10 fresh install, only with restricted ati and broadcom drivers (used in 7.04) 3 min 4 seconds grub enter to login prompt.  And the hd seems to be worken constantly.

PC is a amd athlon 64 3500, 2 gig ram, separate 10 gig partition for 7.04 and 7.10 on same drive, both using the i386 32 bit cd.

Any ideas?

---

### Post by philinux on 2007-10-22
Mines 55 seconds from grub to login.

Saw a thread about this the other day - something about editing the grub kernel line for quiet splash etc.

---

### Post by master_kernel on 2007-10-22
I got 37 seconds from GRUB to login screen using Gutsy (Final Release). It might be faster when I upgrade the kernel with KernelCheck (see the sig). :)

Remove the GRUB option for quiet splash and see what's taking so long.

---


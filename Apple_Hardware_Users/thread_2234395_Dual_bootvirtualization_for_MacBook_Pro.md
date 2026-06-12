---
title: "Dual boot/virtualization for MacBook Pro"
date: 2014-07-14
forum: Apple Hardware Users
---

### Post by agusta2 on 2014-07-14
I have just got a MacBook Pro(i5, 256GB SSD, 8GB RAM, Intel Iris) and i want to use Ubuntu on it for some development work and not very graphic intensive tasks. I would like to know what would be a better option - dual booting or virtual machine(using virtual box). Also, there are different versions on the Ubuntu download page - 64 bit mac AMD64, 64 bit. Can you suggest the version better suited for my MBP. Thanks!

---

### Post by bapoumba on 2014-07-14
*Thread moved to **Apple Users**.*
You will get better exposure here :)

---

### Post by oldfred on 2014-07-14
I do not know Mac, but just saw this. But he installs the bleeding edge or next versions of kernels and video drivers to test future versions.

 Ubuntu With Linux 3.16 Smashes OS X 10.9.4 On The MacBook Air

[http://www.phoronix.com/scan.php?page=article&item=apple_osx1094_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=apple_osx1094_ubuntu&num=1)

Some links to get you started, but some users that have actually installed should post in this thread.
 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)

---

### Post by agusta2 on 2014-07-14
Thanks @bapoumba. Thanks for the links @oldfred, but i would like to know suggestions for dual booting vs virtual machine, and pros/cons of either.

---

### Post by zircon_34 on 2014-07-15
I would recommend using a virtual machine for your task. Installing a dual boot can be tricky. I had no issues with macbook air, more issue with pro. Since your machine is quite performant, I do not see the point of dualboot except if you dont like OS X and plan to work mostly using linux. You can download any iso and install it in your virtual machine. I use the normal 64bit install (xubuntu, ubuntu unity or ubuntu gnome, I tried them all!), never used any mac version and cant recommend it. Linux is fantastic for development work! Have fun;)

---

### Post by agusta2 on 2014-07-15
Thanks @zircon_34 ! i agree with the part of dual boot being tricky, so i think i'll go ahead with a VM for now and as i get more confident with using ubuntu, will try dual booting...I hope you haven't faced any performance lags(low response time etc) with the VM? Are there any considerable performance differences in using a 32 bit guest OS and 64 bit guest OS?

---

### Post by zircon_34 on 2014-07-15
no performance lag, ubuntu is really fast you just need to allocate enough RAM, for example 4GB was already very nice experience for me. I have a macbook air were I could only allocate 2 Gb RAM, unity and xfce run nicely whereas gnome was impossible to run too laggy. with 4 Gb any of the desktop should run nicely. I always use the 64 Gbit version on newer hardware. but I guess You will only see a difference between 32 and 64 bit version if you have >8 Gb RAM as I recall 32 bit only uses max 4Gb. correct me if Im wrong...
 You can just try both it doesnt harm to try in a VM.thats the beauty!

---

### Post by zircon_34 on 2014-07-15
I forgot to mention, I use VMware fusion. I don't know about virtual box. I would be interested about your experience.

---

### Post by agusta2 on 2014-07-20
Finally installed ubuntu on virtual box..working well so far, have to figure out some way to get full resolution(retina standard) on it..but its working pretty smoothly. Assigned 3 gb ram to it.will have to play around with it for a few days to really gauge its performance :)

---


---
title: "yaboot problem..."
date: 2006-10-19
forum: Apple PPC Users
---

### Post by chrluc on 2006-10-19
I have a mac with os x 10.3 installed and used the disk utility in os x to partition the drive and installed Ubuntu on the second partition... it installed ok, all but yaboot... I had no other choice but to finish the installation without installing yaboot. Now I have Ubuntu installed but no way of accessing it. I can access the partition from a live cd and it shows yaboot is installed, but I still don't cant loggin into in... please help.

---

### Post by iAndy on 2006-10-19
You need to partition OS X in a certain way in order for it to be none-volatile to OS X, as well as making it possible for the Ubuntu CD to FULLY install everything you need.

I'm not sure what to do with your current set up, but to get Ubuntu on my PowerBook G4 I followed the steps from here:

[http://ubuntuforums.org/showthread.php?t=89960]("http://ubuntuforums.org/showthread.php?t=89960")

Worked perfectly...although took some time...(i.e.: not seconds like some of the people say!...more like an hour!)

See if you can redo what you have already done using the methods in the included link or see if there is a way to tweak whats in that thread to get your bootloader on properly.

Hope this is of some help!

Good luck!

---

### Post by seatea on 2006-10-20
Did your installer create an Apple Bootstrap partition? If it didn't, I believe you  will have to delete the ubuntu partition partition,leaving it as free space, run  the  installer again, and, if using the Live CD, have  the Live CD installer use the largest continuous free space to install ubuntu. This should create  everything you  need to start up ubuntu. If there is  an Apple Bootstrap partition, then it might help to copy your yaboot.conf from your installed ubuntu partition, if it looks OK, into the Live CD "/etc" folder replacing its yaboot.conf and run ybin -v from terminal. I  don't know if  the latter suggestion  will work. My thinking is that  ybin will use the new yaboot.conf  to fix your  boot problem. I am assuming  that you can't boot to the ubuntu  partition from holding down the option key.

---


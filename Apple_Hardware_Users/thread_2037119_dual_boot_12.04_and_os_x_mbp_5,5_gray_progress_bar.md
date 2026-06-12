---
title: "dual boot 12.04 and os x mbp 5,5 gray progress bar booting into os x"
date: 2012-08-03
forum: Apple Hardware Users
---

### Post by jono1515 on 2012-08-03
I have a macbook pro 5,5 that I set up to dual boot os x snow leopard and ubuntu 12.04. I followed instructions from this post - [http://ubuntuforums.org/showpost.php?p=11889769&postcount=6](http://ubuntuforums.org/showpost.php?p=11889769&postcount=6) because I was originally trying to install Kubuntu. 

Basically, I installed refit, then created a fat partition with boot camp. I booted from the install cd and used gparted to make the fat  partition unallocated. Then I installed Ubuntu and put grub on the ubuntu partition. After rebooting I used gdisk in os x to create a hybrid MBR. Then I rebooted again and used the partition tool in refit to sync the partition tables.

My problem - when I boot into OS X I get a gray progress bar that takes about 6 minutes to go through what I suspect is a disk check before it loads OS X. Happens every time whether or not I've booted from OS X or Ubuntu last. Ubuntu loads fine. And OS X does eventually load each time, it just takes forever.

I've repaired disk permissions from disk utility in OS X, it found errors and fixed them but did not solve my problem. The S.M.A.R.T. status of the disk is verified. I manually flashed an efi update following these instructions - [http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/)
The hard drive in the laptop is new (less than a week old) so I'm doubtful that there is actually a problem with the drive, especially since this only started happening after I finished installing Ubuntu.

I've searched through the forums here and I saw a mention of this problem in one other post that was mainly talking about keyboard backlighting on a macbook air, but haven't seen any discussion on how to fix it. I'd appreciate any input! 

Thanks!
Jono

---

### Post by jono1515 on 2012-08-06
Ok, I did a couple more things and have some more information... I reset the PRAM and NVRAM and still had the problem. So I booted in verbose mode and found the following errors-
Incorrect number of thread records
Invalid directory item count

These were repaired and then fsck rechecked the drive and returned the incorrect number of thread records a few more times, each time followed by a repair. After repairing 4 times the laptop boots into OS X.

Seems like there's something wrong with the drive, but it's funny that this only started being an issue right after I set up Ubuntu on another partition of the same drive.

---


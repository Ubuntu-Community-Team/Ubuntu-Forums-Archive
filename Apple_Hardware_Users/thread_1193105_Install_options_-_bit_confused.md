---
title: "Install options - bit confused"
date: 2009-06-21
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-06-21
I have an intel Mac with a number of external drives (firewire 800 & USB).  I am running Mac OSX 10.5.7 on the Mac and was hoping to be able to run Ubuntu 9.04 on my configuration as well (ie dual boot).  I got hold of rEFIt and installed it and all works fine, it sees my "Macintosh HD" and a separate Mac OS X bootable partition on a firewire drive (created by SuperDuper).  Selecting either via rEFIt works fine.  When I put the ubuntu CD in the drive and try rEFIt it sees that as well.

Now what I was hoping to do was install ubuntu 9.04 on an external firewire disk and give ubuntu the entire disk to itself (in whatever partition type it would like ext4???).  Then use rEFIt to provide me with boot options that now would include the ubuntu 9.04 on the attached firewire drive.

This sounds simple to me a newcomer to the world of ubuntu...is this arrangement possible?  It seems??? feasible to me and so I would appreciate some guidance please from more experience ubuntu users on an intel Mac.  I have seen some threads talking about putting ubuntu on an additional partition on the "Macintosh HD" disk but it would be better to put it on a separate firewire disk partition.

Any guidance would be appreciated as I really like the idea of ubuntu and want to uncover its treasures!

Thanks
Peter

---

### Post by Elfy on 2009-06-21
Have a look here - [https://help.ubuntu.com/community//Boot/ExternalHardDisk/Firewire](https://help.ubuntu.com/community//Boot/ExternalHardDisk/Firewire) and [http://macubuntu.blogspot.com/](http://macubuntu.blogspot.com/)

There's a sticky in the Apple forum - [http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)

I've also moved this thread to the Apple forum.

---

### Post by Richardcavell on 2009-06-21
Short answer is: No, you can only boot Ubuntu from an internal partition.  The instructions referred to by forestpixie should be regarded as experimental, for experts only.

Tell you what you could do, though - have a small internal hard disk partition that boots Ubuntu, and push as much of your filesystem as you can off to the external hard disk.  You can mount an external partition as /usr, for example.

Richard

---

### Post by EvansFive on 2009-06-21
Richard,

Your solution sounds like something that would achieve what I am trying to do...even though with an interim step.

How "small" a partition would I require on my "Macintosh HDD" to boot ubuntu?  I guess this is something I need to set up with Boot Camp?

If I created a parition (or two) on the external firewire drive, how do I tell ubuntu to find it there...and secondly how do I safely move significant parts of the filesystem across to the firewire drive.

Sorry for the basic questions but I have always left Mac OS X stuff where Apple wants to install it and so far I have not had the upgrade problems that I read about in various forums.  Also, I am yet to master ubuntu...hopefully when I get it installed and working the exploration can begin.

Thanks
Peter

---

### Post by Richardcavell on 2009-06-21
1.  My whole Ubuntu installation only takes up 3 Gigabytes.  The /usr component typically takes up about two-thirds of anyone's installation.  I suggest the smallest partition you could comfortably create on your internal hard disk and run Ubuntu from it without issue would be 2 Gigabytes.  Divide your external hard disk into at least two partitions.  Then mount the internal hard disk partition as / (root), the first partition of your external hard disk as /usr, and the second external partition as swap.  You could even create a third external partition, and mount the external partitions as /usr, /var and swap.  If you do this, of course you'll always need the external hard disk attached to run Ubuntu at all. 

2.  In order to mount the parts of your file system externally, you can do it within Step 4 (of 7) during installation from your live CD.  It can also be done manually later on, but do it during installation and you won't be able to make a mistake.

3.  Boot Camp could create the internal hard disk's partition easily enough.  I'd use GParted to create the external partitions, because it understands Linux file systems better.

Richard

---

### Post by EvansFive on 2009-06-21
Richard,

That is very helpful advice indeed, I feel more than confident that I can successfully install ubuntu alongside MAC OS X and make use of my external firewire drive for the bulk of ubuntu and other software I want to install (ie Netbeans & MySQL).

Thank you very much for your advice and time.

Regards
Peter

---

### Post by Elfy on 2009-06-21
I would add that if you are going to split the install onto seperate partitions I would also move /home to a seperate partition. In addition make sure that you don't make any of the partitions too small - there was for instance somewhere on the net instructions for using a /boot partition - the suggested size was much too small and caused issues as soon as there was a kernel update.

Good luck with your install :)

Edit - also meant to say that my install - which has little extras installed comes in at 4.2Gb

---

### Post by Wim Sturkenboom on 2009-06-21
I have a Slackware box with a 2GB and a 80GB HD (both IDE). The 2GB only contains /boot, the rest is on the 80GB. So that approach will work for you as well. The only thing that I'm not sure about is the drivers for your firewire disks.

This is the size of my /boot under Ubuntu 8.04 (i386 version)
```

fortyfourgalena@desktop1:/boot$ du -h
196K    ./grub
67M     .
fortyfourgalena@desktop1:/boot$ ls -l
total 67632
-rw-r--r-- 1 root root  266735 2008-11-24 21:52 abi-2.6.15-53-386
-rw-r--r-- 1 root root  419541 2008-11-25 00:42 abi-2.6.24-22-386
-rw-r--r-- 1 root root  419541 2009-04-02 03:13 abi-2.6.24-23-386
-rw-r--r-- 1 root root  419541 2009-04-15 22:05 abi-2.6.24-24-386
-rw-r--r-- 1 root root   69967 2008-11-24 19:47 config-2.6.15-53-386
-rw-r--r-- 1 root root   80041 2008-11-25 00:42 config-2.6.24-22-386
-rw-r--r-- 1 root root   80030 2009-04-02 03:13 config-2.6.24-23-386
-rw-r--r-- 1 root root   80030 2009-04-15 22:05 config-2.6.24-24-386
drwxr-xr-x 2 root root    4096 2009-05-05 17:14 grub
-rw-r--r-- 1 root root 6828726 2008-11-30 19:33 initrd.img-2.6.15-53-386
-rw-r--r-- 1 root root 8322550 2009-01-08 19:43 initrd.img-2.6.24-22-386
-rw-r--r-- 1 root root 8322105 2008-12-23 02:27 initrd.img-2.6.24-22-386.bak
-rw-r--r-- 1 root root 8322590 2009-04-16 16:56 initrd.img-2.6.24-23-386
-rw-r--r-- 1 root root 8322724 2009-04-11 16:30 initrd.img-2.6.24-23-386.bak
-rw-r--r-- 1 root root 8324256 2009-05-05 17:14 initrd.img-2.6.24-24-386
-rw-r--r-- 1 root root 8324223 2009-05-05 17:14 initrd.img-2.6.24-24-386.bak
-rw-r--r-- 1 root root  103204 2007-09-28 12:06 memtest86+.bin
-rw-r--r-- 1 root root  727244 2008-11-24 21:53 System.map-2.6.15-53-386
-rw-r--r-- 1 root root  883597 2008-11-25 00:42 System.map-2.6.24-22-386
-rw-r--r-- 1 root root  883785 2009-04-02 03:13 System.map-2.6.24-23-386
-rw-r--r-- 1 root root  884133 2009-04-15 22:05 System.map-2.6.24-24-386
-rw-r--r-- 1 root root 1414999 2008-11-24 21:52 vmlinuz-2.6.15-53-386
-rw-r--r-- 1 root root 1848792 2008-11-25 00:42 vmlinuz-2.6.24-22-386
-rw-r--r-- 1 root root 1849880 2009-04-02 03:13 vmlinuz-2.6.24-23-386
-rw-r--r-- 1 root root 1850616 2009-04-15 22:05 vmlinuz-2.6.24-24-386
fortyfourgalena@desktop1:/boot$ ls -l grub
total 192
-rw-r--r-- 1 root root    197 2007-07-17 14:27 default
-rw-r--r-- 1 root root     15 2007-07-17 14:27 device.map
-rw-r--r-- 1 root root   7508 2007-07-17 14:27 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2007-07-17 14:27 fat_stage1_5
-rw-r--r-- 1 root root   8128 2007-07-17 14:27 jfs_stage1_5
-rw-r--r-- 1 root root   5763 2009-05-05 17:14 menu.lst
-rw-r--r-- 1 root root   5361 2009-05-05 17:14 menu.lst~
-rw-r--r-- 1 root root   6804 2007-07-17 14:27 minix_stage1_5
-rw-r--r-- 1 root root   9076 2007-07-17 14:27 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-07-17 14:27 stage1
-rw-r--r-- 1 root root 105428 2007-07-17 14:27 stage2
-rw-r--r-- 1 root root   8764 2007-07-17 14:27 xfs_stage1_5
fortyfourgalena@desktop1:/boot$ 

```If I use a separate boot partition on one physical disk, I usually make them 512MB. That should cater for approximate 25 kernels (if I did my sums correctly on the above data).

---

### Post by EvansFive on 2009-06-21
I was planning to use my LaCie d2 quadra external firewire drive via the firewire 800 port.  So if I understand the responses correctly I can put the following on separate partitions on the external drive - usr, home, swap, var.  I have plenty of space on the empty drive so I will be generous with paritition sizes!

Will I need to do anything special with drivers to use this external firewire disk with ubuntu 9.04?

Thanks
Peter

---

### Post by Wim Sturkenboom on 2009-06-22
Why split all the partitions? You will always find that one partition will be full and the others still have plenty of space.
If you don't have an urgent need for more, I would create the following:
```

/boot   (internal HD)
swap    (see note below)
/       (external HD)
/home   (external HD)

```I'm not sure where to put the swap as I don't know at what point it will be accessed. To play it safe, I would personally put it on the internal HD (but that's due to a lack of my knowledge).

PS I'm not sure about the driver for the firewire disk. For me that would be a trial-and-error approach).

---

### Post by Richardcavell on 2009-06-22
You can certainly put the swap file on the external disk.  For one thing, it's quite unlikely that on a modern computer you would be accessing the swap file at all during bootup.  Secondly, it's mounted early on.

Richard

---


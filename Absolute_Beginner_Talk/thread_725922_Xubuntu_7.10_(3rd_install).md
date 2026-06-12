---
title: "Xubuntu 7.10 (3rd install)"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by mltom on 2008-03-16
Xubuntu runs great for this old Windows user. Glad I changed over.
Question:  
   seems like my system booted up & resides in only the first 34gig of my
   harddrive, see below:

   
   Disk /dev/hde: 34.2 GB, 34219745280 bytes
255 heads, 63 sectors/track, 4160 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1          31      248976   83  Linux
/dev/hde2              32        4160    33166192+   5  Extended
/dev/hde5              32        4160    33166161   8e  Linux LVM

How can I claim either "/dev/hde2 or /dev/hde5"?????
I have 'PartedMagic", but doesn't boot very well & have ordered "gparted liveCD".

Any ideas???????????????
tks
tom

---

### Post by banewman on 2008-03-16
Can you post what
df -h
says regarding hde?

---

### Post by mltom on 2008-03-16
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/mltom--linux1-root
                       31G  2.0G   28G   7% /
varrun                 62M   80K   62M   1% /var/run
varlock                62M     0   62M   0% /var/lock
udev                   62M   72K   62M   1% /dev
devshm              62M     0   62M   0% /dev/shm
lrm                    62M   34M   28M  56% /lib/modules/2.6.22-14-generic/volatile
/dev/hde1           236M   24M  200M  11% /boot


thank U for your help.
tom

---

### Post by jken146 on 2008-03-16
According to fdisk, hde is only 34.2 GB big.

---

### Post by mltom on 2008-03-17
I know its 34gig. My question from my first post is how to activate the rest of the HD?
Look at my first post.

tks
tom

---

### Post by penguinpi.com on 2008-03-17
not sure what you mean by "activate" how did you partition the drive during the install??

---

### Post by mltom on 2008-03-17
Please read my first post here, I know Xubuntu 7.10 is using 34gig.
My question is, how do I claim hde2 or hde3.

So far I cannot create a burn image from my downloaded 'gparted' file.

Is there away Xubuntu can claim my unused disk?

tom

---

### Post by penguinpi.com on 2008-03-18
can you mount the extended partition?

sudo mount /dev/hde2 /mount/disk (or wherever you want)

---

### Post by bigredradio on 2008-03-18
I do not see what is unused? You have a boot filesystem build on a partition hde1 and the root filesystem  build on a Logical Volume. The LVM Volume Group is using /dev/hde5 as a physical volume.

I know you are probably used to only one partition for the OS but unix/linux is different. In your case you have two that are being used (hd1 and hd5).  The other partition (hde3) is the extended partition. You cannot use that either because it is just a logical mapping to the rest of the disk.

See, you can only have 4 REAL partitions on a disk. However, to get around this limitation, you can create an extended partition that takes up a majority of the disk. Then you can create basically as many virtual partitions as you want. (there is a limit, but it's not relevant here.)

So, your disk is being used. There is nothing to spare.

---

### Post by mltom on 2008-03-21
Penguinpi,,sudo mount /dev/hde2 /mount/disk, if I enter the following: 

The return msg says: 'mount: only root can do that'

tks
tom

---

### Post by mltom on 2008-03-21
bigredradio; tks for your msg... 

How do I access(or use) /dev/hde5 Linus LVM????????????????
The other responder penguinpi says to mount it, but I get a return msg that says on the 'root can do that'.
Don't give up on me yet.
tks
tom

---


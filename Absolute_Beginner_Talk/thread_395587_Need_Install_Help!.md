---
title: "Need Install Help!"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by CrucialTK on 2007-03-28
So I've an old dell dimension pc. About 3-4 years old, 384 megs of ram, 1.5 ghz proc. It has two hard drives, an 80 gig and a 160 gig. The 80 gig has windows in a 65 gig partition, and the 160 gig is an NTFS music storage drive.

I created a 10 gigabyte partition to install Ubuntu on, but I cannot get it to install on that drive no matter what I do. It constantly asks for /bin,/boot,/home, or /whatever folders first. 

Is there anyway around this? I have no intention of putting Linux on the 160 gig drive. Thanks for any and all help, I truly appreciate it. I've played with Ubuntu before and was very impressed, so I wanna find a way to get it to work now.

---

### Post by dstew on 2007-03-28
How did you create the partition? Did you make a swap partition? Did you specify the mount points? Did you format the new partition?

My guess is that the installer is asking you to specify the linux file system mount points. You need to select at least one partition to mount as / (the root mount point).

---

### Post by CrucialTK on 2007-03-28
> **dstew said:**
> How did you create the partition? Did you make a swap partition? Did you specify the mount points? Did you format the new partition?

My guess is that the installer is asking you to specify the linux file system mount points. You need to select at least one partition to mount as / (the root mount point).

Everytime I do it basically yells at me. I just wanna use that 10 Gig completely for Linux

---

### Post by jerryrw on 2007-03-28
I would use Computer Management under windows first if you have already created the 10g part to un-format it to empty space prior to doing a Linux install.

If you are concerned about loosing data off the second HD during the install, If you know how to do the jumpers I would disconnect it during the install.

The only two partitions you really need are a / (root) and a swap.  You can use the manual partition option to make sure that Ubuntu puts them where you want them.  swap should = about 1.5 times your ram size in general and give the rest to /.

Remember to BACKUP important data first and have a copy of XP handy in case something goes wrong.

---

### Post by dstew on 2007-03-28
Again, how did you create the partition? Is it formatted?

---

### Post by NicoleM on 2007-03-28
to install linux you need a minimum of 2 partitions.

you need a / partition and a swap partition.

the general rule i hea rabout the size of a swpa partition is about 1.5-2 time the aamount of ram you have.  linux uses this as sort of a virtual ram.

if you had say a 10GB and a 1GB partition and in the installer set the mount point for the 10g as / and the 1g as swap you should be good.

the other mount points are optional, but can also have their uses.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) on the left side of that page the "plan partitions" link and the "install" links should give you a nice walkthrough if I wasn't clear enough here.

---


---
title: "how should i partition my hard drive"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by terminaldestruction on 2007-12-09
Hi,

I am about to install ubuntu for the first time. i don't have a partitioned hard drive at the moment but want to partition it ti install ubuntu. do i have the option to partition the drive during the installation or should i partition it using the program on the live CD before starting the installation?

---

### Post by freebeer on 2007-12-09
Yes, you'll have the opportunity to partition it the way you want, or you can let it choose the default setting.  You might want to give a little thought to how you want it laid out, though.  Here's a linky for you to consider: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by terminaldestruction on 2007-12-09
thats grate information thanks allot

---

### Post by mudguts on 2007-12-09
you'll need to consider the fact that you'll need a SWAP file that is twice the size of your RAM (i.e. 512MB of RAM  = 1024MB of SWAP file)
plus if you do plan on putting another O/S (i.e Windows) on later, You might want to keep 30-40GB available for it 

If you are already running Vista, you can manage the drive and create space for a Ubuntu install.

---

### Post by irish_flu on 2007-12-09
If I'm reading you right, please allow me to explain something for purposes of clarification (I don't want to come of as a know-it-all, I just figure being clear on the terms will be helpful for you later):

Every disk with a filesystem on it already has at least one "partition".  If you have a drive with Windows (NTFS filesystem, or maybe Fat32) then that disk must contain (at least) one partition which "holds" the NTFS filesystem.


Like I said, I'm not trying to come of as a pedant here; I just see a lot of folks making mistakes with that term; it seems like lots of folks are under the impression that a "partition" only comes into play when there's a divide between to filesystems (which, given the name "partition", is an understandable mistake).  It'll make it tougher to read instructions if you're unclear on partitioning, so I try to salt threads like this one with that information.

In other words, don't think of a "partition" as a divider between filesystems.  Think of a partition as something that holds one filesystem.  If you've got multiple filesystems (say, Windows NTFS, an ext3 for Linux, and a SWAP for Linux) you've got three "partitions".  If all you've got is your NTFS windows install, then you've got one "partition".

Have a good day, and good luck with your Ubuntu install! :KS

---

### Post by terminaldestruction on 2007-12-09
i have 512MB RAM, 2GB virtual memory which as far as i understand is the windows equivalent to a swap file so do i keep that the same or should i set it to 1GB and then set up a swap file of 1GB through ubuntu?

---

### Post by freebeer on 2007-12-09
You'll probably want a 1GB swap partition.  This would be a separate partition from the others and is designated as swap space.  The Ubuntu live CD understands the difference and will take care of formatting it properly for you, but you will want to tell it the size you want.

FYI, the Windows "swap" (virtual memory) uses space on your NTFS drive for swap space.  Linux uses a separate partition on your hard drive for the purpose.  A different, but superior approach, IMO.

---


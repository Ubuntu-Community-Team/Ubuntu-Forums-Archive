---
title: "Problems installing w/ dual boot"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by rjgz on 2008-04-06
I'm trying to install Gusty on my Dell Vostro 1500, I got everything working off the LiveCD, so I decided I was going to go ahead and install it.

I have a partition already created, which was the Dell factory "Recovery Partition" in NTFS.

Anyway, i go through the installer until I get to the Partition part, and that's where I'm stuck. I choose Manual and it brings up a list of 4 partitions, which is correct. One for the Dell Diagnostics, One for the MediaDirect, One is Vista and the other one is an Empty NTFS 10gb partition.

I selected the Empty 10gb partition and click next and it tells me I need to define a root or something along those lines, I can't remember now. So I right clicked, went to edit partition and changed the mount point to "/", close that and try clicking next again, this time it turns it into a Swap partition, so I go back into edit and change it to Fat32 and click next yet again, and this time it tells me it can't use Fat32.

I'm pretty much stuck right there. I can still get back into Vista, which is definitely good.

Anyway, I want to install it on the 10gb partition I have WITHOUT destroying Vista. The partition is ready and waiting, I just can't figure out how to get it to install to it without killing off my vista partition.

EDIT: When in Vista in the Computer Management>Disk management do I need to "Delete Volume"? And have a completely unallocated block of disk?

Any help would be greatly appreciated,
Thanks

---

### Post by Moop on 2008-04-06
You can't use fat32 for a system partition and you need a swap and a root partition. You can shrink the 10gb partition to leave room for a 1gb swap partition and create both or you can choose guided use whole disk and then choose the 10gb partition to install to. The installer will create the root and swap partitions.

---

### Post by rjgz on 2008-04-06
So during the installation I should choose Guided - Use Whole Disk, then go into and select the 10gb partition?

I just want to make sure I don't lose my Vista installation, that's really the only thing I'm worried about.

Thanks again,
rjg

---

### Post by rjgz on 2008-04-06
Sctach that, somehow It started installing itself and just wiped my HD :(

Here's where I stand now. I backed up all my information and am about to be sitting on a freshly installed copy of Vista. I'm still going to be installing Ubuntu, but do I need to do it any differently? This time should I use the Guided method or Manual? Since i'm free to make a new partition?

Also, since I am about to reinstall Vista, should I just allocate like a 15gb chunk of my HD to an empty, nonformated space and install it there with the Manual method, or would using Guided be better?

Thanks,
rjg

---


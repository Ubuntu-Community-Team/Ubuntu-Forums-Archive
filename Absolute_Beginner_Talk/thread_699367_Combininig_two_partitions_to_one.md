---
title: "Combininig two partitions to one"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by elmasto on 2008-02-17
Through a series of events, I ended up having the following partitions on my machine
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f21d957

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1259       18427   137909547+   7  HPFS/NTFS
/dev/sda2           18428       19410     7895947+  83  Linux
/dev/sda3           19411       19457      377527+   5  Extended
/dev/sda4               1        1258    10104853+  83  Linux
/dev/sda5           19411       19457      377496   82  Linux swap / Solaris

```
What I would like to have is one NTFS (Vista) partition, one Linux and one Swap. The most obvious way I figured to do it was to delete all the non-windows partitions (because I have a lot of stuff on it) - and I was planning to use the tool built in vista, but I can use QtParted as well, and install Ubuntu anew on the free space. A couple of problems with that
1: I don't know if Ubuntu will detect and use the entire free space
2. I don't know if that will delete the MBR, and if GRUB won't be able to detect even the windows etc.

So, what is the best way to go about that, and have a dual bootable machine with just two partions?
Thanks,

---

### Post by MasterJS on 2008-02-17
Well, first I would suggest going about and backing up any important data that you want to keep, on both Ubuntu and Vista into another computer or disk. Then I boot up into the Ubuntu Live CD and in a terminal type gparted. Here you'll be able to edit all the partitions. I would delete all of them, turning them into unallocated space. Then I would create the partitions that you want. Thing is your gonna need three partitions. One for vista, One for Ubuntu, and one for swap. Turn the first partition into NTFS, the second into "ext3", and the last one into "swap". These are the different filesystems for the partitions. The Swap partition is only going to need about 1 GB. Okay then, its time to install. First install Windows into the first partition. Once that is done, boot back into the live cd. When asked where you want to install it (i think its about Step 4), click Advanced. It'll detect all your partitions. Now, the first partition will be Vista so we will leave that one alone (make sure its the first so you don't accidentally delete it). Then click the second partition, which should be the one you made for Ubuntu and hit edit. You assign it the mou nt point of "/" (without quotations), which this the root directory. You'll give it the filesyste "ext3" and then you'll hit ok. Then your gonna need to select the partition and hit format. Okay, now your gonna select the 1 GB partition and hit edit. Here, your gonna have to choose filesystem "swap" and hit ok. I think you'll need to format it and then hit next. Ubuntu will then install itself as normal. To access either one, just hit escape when the GRUB menu appears.

---

### Post by elmasto on 2008-02-17
Hi,
I was trying to figure out a way to do that with out having to reinstall windows.
Thanks,

---


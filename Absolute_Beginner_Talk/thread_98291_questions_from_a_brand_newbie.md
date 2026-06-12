---
title: "questions from a brand newbie"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by jimrz on 2005-12-02
Hi...I am brand new to both ubuntu and linux, except a little playtime with live cd's and watching these forums for a while. My comp = P3 1Gb  512Mb ram currently has 2 older small slow hd's running win 2k. This weekend I am planning to upgrade to a 200 Gb 7200rpm drive and then install dual boot ubuntu/win xp (yeah, I know but have several programs I need for my work that ONLY work on the dark side + I will need to install Intel's Application Accelerator [mb = D815EEA2 and have already updated the BIOS] to be able to fully utilize the new drive) and I have some questions about preparing the system for the new OS's:

- can the swap partion for either ubuntu and/or win xp be placed on a logical drive or do they each need to be on a primary partion of their own?

- along the same line, I would like to put ubuntu root on it's own primary partition and have /home on another. Can I put /home on a seperate 
logical drive?

- since hda0 will be win xp, does ubuntu / then need to be the last partion on the drive or does /'s position on the drive matter?

   Ideally,what I would like to have for drive configuration would be:

hda0 - ntfs - win xp
hda1 - extended - /home. ubuntu swap, win swap, + whatever
hdax - ext3 - ubuntu / (or should this be a different file system?)

This would allow for a small 3rd primary for later use (or just leave a small unallocted space for one).

  Any and all help/ideas will be greatly appreciated.

Don't go away folks, Im sure I'll will be many more questions, shortly.   ;)

---

### Post by Qrk on 2005-12-02
Your scheme looks to work.

I believe / must be a primary partition, but it can be anywhere on the drive. (actually, you could make /boot instead, but it doesn't really  matter)

Home can be anywhere, even on a second hard drive. 

XP doesn't have a swap partition, it uses swap on the partition it is installed on. Unless you mean a, say fat 32 partition for switching files, which can also be anywhere. Ubuntu needs a swap partition (formated as "swap") which you can make when you install it.

Lastly, ext3 is the best choice file system for you to use. Others will work, but its not really a big issue.

---

### Post by kjcon on 2005-12-02
I'm not sure but I think that the swap has to be on a primary partition of its own. 

I think it's a very good idea to set up a seperate /home partition. This allows you to re-install Ubuntu, if necessary, without losing your data and customized settings. 

I like to use extended/logical partitions for everything I can. It makes future expansion easier because you are not limited to four partitions. 

The only things you need a primary partition for is Windows. It has to be the first partition on the disk--hda1, and possibly the swap area.

I would also suggest that you set up a VFAT partition of a few gigabytes to use as a Drive D in Windows so you can transfer data between the two operating systems. Linux cannot write NTFS partitions and Window can't even see any kind of non-Windows file system.

Here is how I've set up my 160 GB drive.

hda1    primary   NTFS      Windows Drive C:          5GB
hda2    primary   VFAT       Windows Drive D:          5GB
hda3    primary    swap      Ubuntu swap                1GB
hda5    extended ext3       Ubuntu /                     10GB
hda6    extended ext3       Ubuntu /home           100GB

The rest is unpartitioned free space.

---

### Post by jimrz on 2005-12-02
[QUOTE=Qrk]Your scheme looks to work.

I believe / must be a primary partition, but it can be anywhere on the drive. (actually, you could make /boot instead, but it doesn't really  matter)

Home can be anywhere, even on a second hard drive. 

XP doesn't have a swap partition, it uses swap on the partition it is installed on. Unless you mean a, say fat 32 partition for switching files, which can also be anywhere. Ubuntu needs a swap partition (formated as "swap") which you can make when you install it.

Lastly, ext3 is the best choice file system for you to use. Others will work, but its not really a big issue.[/QUOTE]

Thanks....my mb is maxed out at 512Mb ram. Not usually an issue, but ...
On win2k I created a swap partion (primary since I had only the 1 partition prior) using PartitionMagic to supplement the ram, which I figured was better than getting into virtual memory. Was hoping to do same w/ xp or, if can't, possibly throw 1 of my old drives back in and put i there or maybe get a pci flash mem adaptor and use it.

   What about the ubuntu swap, does it need to be a primary partion?

---

### Post by jimrz on 2005-12-02
Thanks... I'm thinking I will now probaly throw 1of the 18Gb drive I had been using back in and do the swap thing for win[FAT] and the rest of drive FAT32 for exchange between win/ubuntu and maybe some backup.

---


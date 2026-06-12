---
title: "Procedure for returning to dual-boot setup?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by fender83 on 2008-01-08
Hi all,
I have a Thinkpad T40 (1.5ghz, 512mb ram, 40gb hd) that is happily running linux on it and nothing else.  I have it partitioned with an ~8gb root folder, swap, and ~30gb /home drive. I kept the hidden partition that has the WinXP recovery on it, and still have a Windows CD.

For work purposes, I need to put WinXP back on my laptop. I won't need much space past the basic install - it's mainly for running a few specific programs that won't work in WINE. There are lots of posts about going from Windows to dual-boot, but I can't find much about going from 100% Linux to dual-boot.  What steps do I need to follow in order to:
[LIST]
[*]reformat my partitions (I'll just make linux all on one partition for simplicity, but I might like a storage partition for sharing files between OSes)
[*]reinstall WinXP
[*]fix my MBR/GRUB to handle this
[/LIST]

In what order do I perform those tasks? How do I go about returning to a dual-boot setup? I am not concerned about keeping any data on my current setup - I am more than willing to wipe it all clean to start this process (that is, I don't need to keep my current linux installation).
Thanks in advance for your help!

---

### Post by durrell on 2008-01-08
The easiest way is to reinstall Windows, then reinstall Ubuntu after Windows. That way you ensure that GRUB is setup by the Ubuntu installer.

If you want to format pre-Windows install you can either use the Ubuntu LiveCD or you can use the Gparted Live CD. I prefer the Gparted route, but that's just me.

Since you don't want to keep any data, just install a clean install of Windows XP, then use the Ubuntu Live CD to partition how you want it setup.

---

### Post by logos34 on 2008-01-08
> **fender83 said:**
> I have it partitioned with an ~8gb root folder, swap, and ~30gb /home drive. I kept the hidden partition that has the WinXP recovery on it, and still have a Windows CD.

You can only have four primary partitions on a disk, or 3 + 1 extended partition.  

So if you want to keep the recovery partition then you'll have to make an extended to hold at least two of your linux partitions (say, /home and /swap).

---

### Post by fender83 on 2008-01-08
> **durrell said:**
> The easiest way is to reinstall Windows, then reinstall Ubuntu after Windows. That way you ensure that GRUB is setup by the Ubuntu installer.

If you want to format pre-Windows install you can either use the Ubuntu LiveCD or you can use the Gparted Live CD. I prefer the Gparted route, but that's just me.

Since you don't want to keep any data, just install a clean install of Windows XP, then use the Ubuntu Live CD to partition how you want it setup.

Does Windows need a specific location on the disk (does it need to be first) and will it recognize partitions created by GParted?  Do I need to format it as NTFS before installation or will the Windows installer do that for me?

Would I make the partitions before installing WinXP, or do I make one big ntfs partition, install WinXP, and then have the Ubuntu installer resize the partitions again?

Thanks again!

---

### Post by Moop on 2008-01-08
XP won't see a ext3 partition. Use the live cd to create the partition you want for XP and then install XP. 

Then use the live cd to create your partions for Ubuntu. You can put them all inside a extended partition. When you install ubuntu choose the manual option when it comes to the partitioner and install to the partitons you created. You can choose the mount points for / 
/home and swap.

---

### Post by durrell on 2008-01-08
Just tell the Windows installer to format the entire disk, then go back in after it is installed and install Ubuntu. Ubuntu can be used to do the partitioning later.

---

### Post by fender83 on 2008-01-09
Just to clarify it, these are the steps?

[LIST=1]
[*]Use GParted to format the entire disk as NTFS
[*]Reboot and install WinXP, which will rewrite my MBR (getting rid of GRUB)
[*]Install Ubuntu, which will take care of creating/resizing partitions on my hard drive
[/LIST]

I'll test it out soon and report back - thanks so much!

---


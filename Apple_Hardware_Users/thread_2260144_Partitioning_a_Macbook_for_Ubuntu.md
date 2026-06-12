---
title: "Partitioning a Macbook for Ubuntu"
date: 2015-01-09
forum: Apple Hardware Users
---

### Post by rbengr on 2015-01-09
I have a Macbook that is currently dual partitioned, using Boot Camp.  Can I repartition into 3 areas?  One each for OS X, Windows and Ubuntu.  Will I sti&#322;l use Boot Camp or something else?  Thanks.

---

### Post by slickymaster on 2015-01-09
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by este.el.paz on 2015-01-09
> **rbengr said:**
> I have a Macbook that is currently dual partitioned, using Boot Camp.  Can I repartition into 3 areas?  One each for OS X, Windows and Ubuntu.  Will I sti&#322;l use Boot Camp or something else?  Thanks.

@r:

My personal experience says "No" & "No" . . . but your experience may be different.  I had my MBPro set up for dual-boot using Bootcamp as per recommended on the web, but when I went to add a third partition the HD was "locked" . . . I believe by BC.  I had to boot from a clone (or install disk) on extHD, wipe the drive clean; and then I used Disk Utility to set up three partitions, and I use rEFInd as the Boot selector following the "rodbooks" instructions online in the OSX partition, which is installed first.  Haven't done the Windows thing, but I think that's number 2, and then add linux last . . . you could try, "install into largest free space" if that option shows, otherwise in the installer choose "something else" and when GParted window opens, set up three partitions, small one for "bios_grub", the largr one for "/" formatted ext4, and 1 - 2x RAM for swap.

e.e.p.

---


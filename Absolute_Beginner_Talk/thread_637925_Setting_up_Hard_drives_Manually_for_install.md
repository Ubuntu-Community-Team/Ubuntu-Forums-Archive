---
title: "Setting up Hard drives Manually for install"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by WElliott on 2007-12-11
Having a terrible newbie moment here... Here's what I have:

2) 160Gb hard drives, SATA on mobo  (sdb & sdc)
3) 250Gb hard Drives, SATA on Adaptec PCI card (sda)

What I am trying to figure out is if I set this box up running 7.10 server and VMWare server how do I manually configure these drives for the best return?  I.E. put a boot partition and swap on sdb and then make the remaining drives (sdc & sda) available for max file storage of images, etc.? Also, where should the mount points be in this instance? and finally ext3 or ext2 for the file storage area?

Any advice would be greatly valued! Sorry about the complete noob question!

---

### Post by Pforrest on 2007-12-11
The easiest way for you to install is select existing partition-in your case sdb-assuming it's a least 50% of the total disk space(160GB) since you'll also run VM. Let Ubuntu do it own thing for now and do select to install to the MBR of the 160GB
As to format style (ext3 or ext2) at this time just take default. As you're progress you will form your own opinion after experimentation.

Good Luck to you.

---

### Post by WElliott on 2007-12-12
Thank you for the insite PForrest!!  Much appreciated

---

### Post by mmcmonster on 2007-12-12
> **WElliott said:**
> Having a terrible newbie moment here... Here's what I have:

2) 160Gb hard drives, SATA on mobo  (sdb & sdc)
3) 250Gb hard Drives, SATA on Adaptec PCI card (sda)

What I am trying to figure out is if I set this box up running 7.10 server and VMWare server how do I manually configure these drives for the best return?  I.E. put a boot partition and swap on sdb and then make the remaining drives (sdc & sda) available for max file storage of images, etc.? Also, where should the mount points be in this instance? and finally ext3 or ext2 for the file storage area?


No one should really be using ext2 anymore.  Ext3 is as stable as it gets, and works fine for general daily tasks (You may get slightly better performance with reiserfs or something else in certain edge (rare) cases.).

From general experience, here are some good thoughts about filesystem management:
/ (root) should be ~10GB
/swap should be (at most) twice your physical ram.
/home should be as large as you can possibly make it

So, in your particular situation, I would do something like this:
sdb1 - ext3 - 10GB - /
sdb2 - swap - 1GB - swap
sda1 - ext3 - 250GB - /home
sdb3 - ext3 - 149GB - /home/extended1
sdc1 - ext3 - 160GB - /home/extended2

When I install vmware, I would then tell it to store the virtual filesystems in /home/extended1.

Once you get more experienced, you may want to take a stab at a logical volume management (LVM) system, such as [EVMS]("http://evms.sourceforge.net/").  That being said, I don't think Ubuntu has a nice way of setting that up for newbies (and I consider myself a newbie with logical volume management things).

---

### Post by WElliott on 2007-12-12
MMCmonster... Thank you so very much. That is just the summary I was looking for!! Thanks for helping me out on this.

---


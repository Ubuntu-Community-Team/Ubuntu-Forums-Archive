---
title: "Dual Boot Partition Question"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by 3pinner on 2008-02-02
I am getting ready to install ubuntu 7.10
Dual boot with Windows 2000.
Ubuntu will live on its own hard drive.
I will partition the new disk manually.

I want to partition the hard drive so that I have the necessary partitions for Ubuntu (Root and swap  at least) but want to also have a FAT32 partition as well that I can copy or move my documents, Browser bookmarks etc onto it, so I can migrate them to Ubuntu later.

Any suggestions?

Thanks
3pinner

---

### Post by ugm6hr on 2008-02-02
Why not just have  /, /swap and /home (all ext3) partitions.

You can copy files to ext3 partitions from Windows if you use [http://www.fs-driver.org/](http://www.fs-driver.org/)

Or you can read the Windows 2000 partition directly from Ubuntu.

A FAT partition is probably unnecessary.  Of course, if you *really* want a FAT partition - just create it with GParted (Partition Editor) from the Ubuntu LiveCD prior to installing.

If you have 2 hard drives - I'd recommend you put the new Ubuntu HD as the first HD in boot priority, and ensure that Grub is installed on the MBR of the Ubuntu drive.

---

### Post by 3pinner on 2008-02-02
Thank you ugm6hr,
I like the idea of making the Ubuntu HD as the first in boot priority, and ensure GRUB is installed on the MBR of the UBuntu drive.
Will that be included in the install Wizard at some point?
I assume I should physically install the new drive as the Master  before I begin the install?
(Both of these drives are SATA disks)
Will I be able to format a FAT32 partition on that new drive at a later date, or does it make more sense to do that on the Windows drive using Windows to accomplish that??

thanks again!

---

### Post by Moop on 2008-02-02
Sata hard drives don't have a master and slave setting. Just set the bios to boot the new hard drive first and grub will install there. 

If you want a fat32 partition you may as well create it now but it could also be created after you install Ubuntu. Gparted will work fine, no need to do it from windows.

---

### Post by ugm6hr on 2008-02-02
> I like the idea of making the Ubuntu HD as the first in boot priority, and ensure GRUB is installed on the MBR of the UBuntu drive.
Will that be included in the install Wizard at some point?
Boot priority has to be set from the Motherboard BIOS.
The install Wizard offers option of where to put Grub in the "Advanced" tab.  The default is (0,0), which is the first hd (sda in linux-naming terminology) - which should already be correct if you install as Master.

> I assume I should physically install the new drive as the Master  before I begin the install?
(Both of these drives are SATA disks)
That would be my recommendation.  And set the BIOS to boot from it.

> Will I be able to format a FAT32 partition on that new drive at a later date, or does it make more sense to do that on the Windows drive using Windows to accomplish that??
If you do want a FAT partition - I would *create* it prior to installing Ubuntu.  Then reformat it from Windows before using that partition.  GParted can format FAT, but I always get confused about the difference between vfat, fat16 and fat32 - easier to just let Windows decide!

---

### Post by 3pinner on 2008-02-02
thank you both for the help.
One final question:
If Iload  Ubuntu on the first hard drive as suggested, and allow GRUB to install in the MBR of that hard disk, will that in any way affect the MBR of the Windows drive, which will now be the second hard disk (slave)?

If I have any problems with the install in this case, will I just be able to remove the UBUNTU drive and reinstall the Windows drive as the master, and boot to windows as usual?
(not that I really WANT to mind you............ just covering my butt since my wife uses windows for now :-)

---

### Post by 3pinner on 2008-02-02
Sorry, I would like to know the answer to the last post before I move on if possible.
thank you for the assistance!

---

### Post by louieb on 2008-02-02
> **3pinner said:**
> ...If Iload  Ubuntu on the first hard drive as suggested, and allow GRUB to install in the MBR of that hard disk, will that in any way affect the MBR of the Windows drive, which will now be the second hard disk (slave)?...reinstall the Windows drive as the master, and boot to windows as usual?:-)

Your widows drive should remain untouched. And an entry to boot XP should be automatically added to the GRUB boot menu.    

If you have any doubt Just unplug your windows drive before doing the install. Then its just a matter of manually adding a windows entry to /boot/grub/menu.lst 

It will look something like this:
```

title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
      boot


```[Nuts on Grub]("http://louboldt.com/ilinuxgrub.htm")

---

### Post by ugm6hr on 2008-02-03
> **3pinner said:**
> If I have any problems with the install in this case, will I just be able to remove the UBUNTU drive and reinstall the Windows drive as the master, and boot to windows as usual?
(not that I really WANT to mind you............ just covering my butt since my wife uses windows for now :-)

As long as you install Grub on the Ubuntu HD MBR, Windows HD MBR will be untouched.  So all you would have to do is remove the Ubuntu HD, and it would work.

If you are unsure, just do as louieb suggested; that will ensure that the Windows HD is not written on to (by accident).

---


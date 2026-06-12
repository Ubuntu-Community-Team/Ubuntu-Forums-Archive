---
title: "Uninstall Ubuntu?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by goptl on 2006-07-07
How would I go about uninstalling Ununtu 5.10 from WIN XP Home?

Is there a easy way to delete the partition that it is installed so that I can get all the disk back for XP?

Thank you.

---

### Post by Dr. Nick on 2006-07-07
Their is a program in XP Pro (not sure on home) to delete partitions, It buried in the administratve tools section of the control panel somewhere. 

If you want to get rid of ubuntu get your XP disk and boot from it. Before installation takes place you should see a option to get a "Recovery Console" Its on one of the blue screens, probably after the EULA. Go into that and run fixboot and/or fixmbr to restore the windows loader and erase grub.

---

### Post by catlett on 2006-07-07
You will have to re-install ntldr (windows bootloader) before you erase Ubuntu because grub exists in ubuntu's partition. You can do this fron the recovery console  in XP. The problem is the great minds of microsoft made the recovery console accessable only from the XP installation disk. So you need an XP install disk. Boot into it and choose the recovery console option. When you finally get to the command prompt a.k.a. C:\ enter ```
fixmbr
``` This will rewrite the mbr so you can boot to windows with the Windows boot-loader,
Reboot your computer to make sure the changes take effect. Then go into the control panel. Enter performance and maintenance and get to administrative tasks. When you get there look for the device manager. Then look for disk management. There it will have options for defragmenting and formatting. It will show you a graph of your drive and it will have ubuntu's partition. Select it and choose the option to "convert" the drive to ntfs.
That;s it. Ubuntu will be gone. You will be able to boot to windows and you will have a second ntfs partition reformatted and ready for data or whatever else you want.
You could re-size your windows nets to the size of both partitions if you wanted to. It's just a matter of preferencP.S.

---

### Post by Frank Golden on 2006-07-07
> **Dr. Nick said:**
> Their is a program in XP Pro (not sure on home) to delete partitions, It buried in the administratve tools section of the control panel somewhere. 

If you want to get rid of ubuntu get your XP disk and boot from it. Before installation takes place you should see a option to get a "Recovery Console" Its on one of the blue screens, probably after the EULA. Go into that and run fixboot and/or fixmbr to restore the windows loader and erase grub.
Read the tutorial

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

It has a section at beginning about removing Ubuntu. Restore the MBR using the method described above or in tutorial.Then in XP
right click My Computer and choose manage from the context menu
and then Disk Management or type diskmgmt.msc in start>run.
Locate the linux partition right click and delete. You can then
right click the unallocated free space and choose create and format to use the resulting space. You really don't need a third party partition manager for these simple tasks.

Update: Catlett's post is essentially the same as mine. He got done typing
before I did. LOL
I prefer to delete the Linux partition first then format to NTFS in a separate step. If you have Partition Magic you can format to Fat 32 if you like.

---

### Post by ZombiekE on 2006-07-08
Thank you guys. I'm going to try it. I had installed Ubuntu on my 2 desktops and 1 laptop and eventually I'm going to keep it just in my laptop.

Reason: I've found that although this is the best distribution I've it still needs to be more user friendly. I am leaving home next month and I can't leave my parents with this OS. I installed some things in my harddisk, it became full and then, then I couldn't enter the graphics mode again. If this happened to my parents it would keep the computer unusable (luckily they have dual boot, but I've decided to remove it entirely because I don't think Linux is still reliable enough for the average user). I'll however keep it in my laptop (I'm moving out with it) and it'll keep being my primary OS. Ironically, I feel very comfortable in Linux, more than in Windows XP now.

---

### Post by sankarv on 2006-08-07
I too is using XP on my, machine. It does not have any options for partition manipulations.

All you need is a Partition manager which is frequenly usable.


The best partition manager is GParted which you can burn as Live CD and use whenever you want. Its handy less than 50 MB and is highly reliable for partition add/delete operations. You can restore windows as said by
Dr. Nick and catlett,

Then proceed with this.

Always have a GParted CD with you because it follows same procedure for deleting any type of OS.

---


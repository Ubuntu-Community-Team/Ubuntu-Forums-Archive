---
title: "Could use some help from experienced users"
date: 2011-08-17
forum: Any Other OS
---

### Post by RageFurby on 2011-08-17
Okay, so I'm fairly new to ubuntu. I haven't been using it long. My computer is not old I just think that it has a terrible virus.

I can install ubuntu fine, and it runs for about a day or two then it just stops working. It won't read any of the drives right, starts trying to fix errors, and what not. Again the computer isn't old, it's a Dell Inspiron 1545, I went to try and reinstall windows onto the computer but it says that the Partitions need to be formatted to NTFS, but I don't know the first thing about getting something like this completed.

I've looked for other tutorials online, saw some people that had similar issues but couldn't find an apt solution. I'm just tired of ubuntu failing on me. I tried installing previous versions of ubuntu as well and after a few days it seems like the drivers just start erasing themselves and failing or damaging themselves or something. Because I start getting a bunch of errors I can't remember the errors offhand. So don't ask what the errors say, it just talks about fixing ****, and tmp and crystalswap1 errors and it starts losing files and stuff. I don't know and will not be able to look at what the errors are probably until tomorrow. Fact of the matter is I'm tired of dealing with it and want Windows back.

Windows doesn't want to load again because it doesn't have a formatted NTFS Partition so if you know what you're doing then please give me some help and advice here.

Thanks.

---

### Post by Drakx on 2011-08-17
> **RageFurby said:**
> Okay, so I'm fairly new to ubuntu. I haven't been using it long. My computer is not old I just think that it has a terrible virus.

I can install ubuntu fine, and it runs for about a day or two then it just stops working. It won't read any of the drives right, starts trying to fix errors, and what not.

I'm just tired of ubuntu failing on me. I tried installing previous versions of ubuntu as well and after a few days it seems like the drivers just start erasing themselves and failing or damaging themselves or something. Because I start getting a bunch of errors I can't remember the errors offhand. So don't ask what the errors say, it just talks about fixing ****, and tmp and crystalswap1 errors and it starts losing files and stuff. I don't know and will not be able to look at what the errors are probably until tomorrow. Fact of the matter is I'm tired of dealing with it and want Windows back.

Thanks.

I've had problems like this before turns out the Harddrive was about to die on me (your computer may not be old in terms of when you bought it but that does not mean all the components are brand new that day and/or working as they should be.

How ever failing sending it back the shop to get them to look at the HDD (Hard drive) I would at least try to post some of the errors your getting.

---

### Post by fdrake on 2011-08-17
if you can get your hands on a ubuntu live cd , boot your computer from it. user Gparted application (from the System tab) and format your HDD to FAT or NTFS filesystems. (make sure you backup your needed data first!)  Install windows and the install Ubuntu ,

---

### Post by 23dornot23d on 2011-08-17
Similar thoughts ..... on the subject ..... 

( I cannot think of any time where parts of my Data just go missing - unless the Hard Drive is faulty )

The hard drive may be the problem here ... not the OS ...... but to prove it to yourself .....

Use a Partitioner using a bootable CD ....... [COLOR=Red][**List of Partitioners**]("http://en.wikipedia.org/wiki/List_of_disk_partitioning_software")

or google search for partitioning for Winodws ?? XP VISTA WINDOWS7 ....
[/COLOR]
( TAKE YOUR DATA OFF FIRST OR BACKUP ANYTHING IMPORTANT TO YOU )

This next step will clean out the drive or a part of it  ......

Format the drive as NTFS

Get a Windows Install CD / DVD

Load Windows back on from an official install CD / DVD .......

Reboot ....

---

### Post by drawkcab on 2011-08-18
> **Drakx said:**
> I've had problems like this before turns out the Harddrive was about to die on me (your computer may not be old in terms of when you bought it but that does not mean all the components are brand new that day and/or working as they should be.

How ever failing sending it back the shop to get them to look at the HDD (Hard drive) I would at least try to post some of the errors your getting.

If you submit your computer for warranty with Linux installed, the store/manufacturer will often claim that you've violated the warranty.  This is BS but it happens often enough.  Reinstall Windows before exercising your warranty.

---

### Post by drawkcab on 2011-08-18
I also agree that this could be failing drive.

I recommend booting into a live usb session and dloading gparted.  Use gparted to format your hdd back to ntfs.  You can then install windows over ntfs.

Log into windows and see if the same thing happens.  If so, you've got problems with your hardware, not ubuntu.

Best of luck.

---

### Post by Drakx on 2011-08-22
> **drawkcab said:**
> If you submit your computer for warranty with Linux installed, the store/manufacturer will often claim that you've violated the warranty.  This is BS but it happens often enough.  Reinstall Windows before exercising your warranty.

No one said you should take it back with Linux or windows for that matter.

---

### Post by oldos2er on 2011-08-22
> **RageFurby said:**
> Windows doesn't want to load again because it doesn't have a formatted NTFS Partition so if you know what you're doing then please give me some help and advice here.

I think you should start with some basic troubleshooting e.g. running memtest (should be available from the grub menu, if you still have Ubuntu installed), and allow it to run overnight.

If you can boot into recovery mode, install smartmontools and let it test your hard disks.

---


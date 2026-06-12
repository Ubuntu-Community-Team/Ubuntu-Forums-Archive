---
title: "Big Problem"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Yizi on 2007-09-14
I Reinstalled my Windows XP with was dual boot with Ubuntu, now it's finish. I don't have any dual boot menu options and when i try to load Ubuntu (from secound hard drive) it wont let me it gives an error:

```
**The operating system is not able to start.**
```

**[COLOR="Red"]HELP![/COLOR]**

---

### Post by kellemes on 2007-09-14
Get a copy of supergrub and reinstall your bootloader (grub)

---

### Post by Yizi on 2007-09-14
I don't have any idea how to do that!

---

### Post by vambo on 2007-09-14
> **Yizi said:**
> I don't have any idea how to do that!



[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Have a look here

---

### Post by w4ett on 2007-09-14
> **Yizi said:**
> I don't have any idea how to do that!

Don't Panic.....when you reinstall Windows it overwrites the modifications in the MBR of the drive....the Super Grub disk is here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by steevols on 2007-09-14
> **kellemes said:**
> Get a copy of supergrub and reinstall your bootloader (grub)

You just inadvertently helped me a ton. Thanks!

---

### Post by Yizi on 2007-09-14
OK, i did what all of you said it said successful and after i reboot the pc the menu option didn't came up, i used F8 to bring up the boot option and booted from the secound hard drive which is Ubuntu bur it gave a error saying:

```
The selected option cannot be mount
``` 

What shall i do next?

---

### Post by Yizi on 2007-09-14
I managed to access the menu from SGD but still wont show up at the start, am i doing something wrong?

---

### Post by w4ett on 2007-09-14
Instructions from the Super Grub Disk:

> I reinstalled Windows and Linux no longer boots.

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3. Gnu/Linux
   4. Fix Boot of Gnu/Linux (GRUB)
   5. select your Linux partition
   6. see message, 'SGD has succeeded'
   7. you're done! reboot

See:


[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no)

---

### Post by larry Gaminde on 2007-09-14
Go to this site it's all you need to know about fixing GRUB
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Yizi on 2007-09-14
> **w4ett said:**
> Instructions from the Super Grub Disk:



See:


[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no)

I did exctly this! it's not coming up with the menu options :cry:

---

### Post by SunnyRabbiera on 2007-09-14
Hmm... it might be best to back things up and re install ubuntu and have it set for dual boot.
its stuff like this is why many suggest you install windows before installing linux

---

### Post by Yizi on 2007-09-14
I had problems with my Windows thats why i reinstalled it, how do i back up everything specialy my firefox settings?

---

### Post by Yizi on 2007-09-14
Is there anyway i can access my Linux (second hard drive) from Windows and take some files out?

Because i can't copy any files to Windows, it says i don't have any permission to do that.

---

### Post by Yizi on 2007-09-14
anyone :-s

---

### Post by displicente on 2007-09-14
I don't know in what shape is the master boot record (or what ever mbr stand for) afetr running utilities for grub.

Some time ago, I did the same. Installed Windows after Linux and startup went crazy. At that time I found a web site saying that you should boot with a win98 disk and give a command fdisk mbr
this reconstruct the mbr and you got grub again. It worked nicely. I even have a problem with windows, in which the OS decided to repair itself and destroyed the original mbr, and this get back the grub again. The only catch is having a bootdisk ... That's why I keep one safe for emergencies.

This will work fine for fat32, winXP is installed in NTFS by default. I hope this will help you, as you can look for a utility that let you reconstruct a NTSF mbr.

Neville

-------------------
don't follow me, as I am lost too.

---

### Post by logos34 on 2007-09-14
> **Yizi said:**
> Is there anyway i can access my Linux (second hard drive) from Windows and take some files out?

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by displicente on 2007-09-14
About getting your files, What I would do is to boot the computer with a live cd. 
Then copy the files to a USB memory stick or burn them to a CD-R

Neville

-----------------
don't follow me, as I am lost too.

---

### Post by Yizi on 2007-09-14
My menu options is fixed i took the risk and manualy did it, thanks everyone, but i can't transfer those files to my USB memory, it says:

```
You do not have permissions to write to this folder.
```

---

### Post by Tyke91 on 2007-09-14
I've also had this problem, not only does it get rid of grub, it messes up windows a bit.


before you reinstall grub, put your windows disk in and run CHKDSK (meh... no idea why windows commands are so loud :( ) from their command line.

---

### Post by gordonh on 2007-09-17
> **Yizi said:**
> Is there anyway i can access my Linux (second hard drive) from Windows and take some files out?

Because i can't copy any files to Windows, it says i don't have any permission to do that.

I can't remember if this is how I did it, but I've got windoze permanently mounted and can read/write with no problems.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions)

I seem to remember that I had to change permissions.

NB I've since deleted all windows related stuff from the drive and just use it as another drive.

However, it doesn't respond to gparted and I'd like to shrink it and make the "normal" linux drives bigger.  Does anyonr have a solution?

---


---
title: "(X)ubuntu and Win8 -- possible on 60 GB?"
date: 2013-09-24
forum: Any Other OS
---

### Post by Pako Pako on 2013-09-24
Probably overhtinking things, but I wanted to be sure.

I've got an old laptop that runs Win8 that I just moved to a 60GB SSD. Since that was a success, I figure a simple liveCD and DD should work in case I screw something up?
```
dd if=/dev/hda of=/home/hda.boot.mbr bs=512 count=1 
dd if=/dev/sda1 of=/home/sda1.bin bs=1024
```
Problem I have now is, Win8 is taking up 70% of the HDD (with about 5GB of leeway). Can I install (x)ubuntu and take up the remaining 20GB and not bork the Win8 portion?

I'm also a total newbie with Win8; the only backup I have is off a failing HDD and the image I'll be making.

---

### Post by oldfred on 2013-09-25
Might be better to use Windows backup tools.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by UltimateCat on 2013-09-27
just a thought-;)

You may want to shrink your Windows partition before you install your Linux distro.

Before I installed Fedora I had to shrink my Windows 7 partition.

---

### Post by Pako Pako on 2013-10-02
> **oldfred said:**
> Might be better to use Windows backup tools.
[Backup windows before install](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710) [using Macrium by Mark Phelps](http://www.macrium.com/reflectfree.asp) or [DriveImage by srs5694](http://www.runtime.org/driveimage-xml.htm)
I'll probably make my own made-within-OS recovery disk using [one of](http://forums.techarena.in/guides-tutorials/1114725.htm) [the many](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html) [methods provided](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/) -- I might as well do it before 8.1 rolls in and disables that feature.

But I still stand by using DD to image the entire drive in case I screw up; this way I just re-DD everything (MBR and all) even if it takes longer.

> **UltimateCat said:**
> You may want to shrink your Windows partition before you install your Linux distro.
Using tools within Windows8 right? (And not via gparted off a Linux LiveCD.) My only worry is that there isn't much wiggle room. I'm not sure how much bloatware I can take out (or even what to look for any more) to reduce it below 35 GB so that I can partition the drive into a 45 / 15 split.

And then I have to hope Win8 and Ubuntu (even relegated to the back 25% of the drive) will play nice?

---


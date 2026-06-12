---
title: "Backing up Files"
date: 2012-01-01
forum: Any Other OS
---

### Post by chris1216 on 2012-01-01
All,

Let me tell you what I did, and what I want to do to fix it and someone tell me if this is a good idea or if there is a better way.  I have a lap top with Windows 7 on it.  I installed Mint in a dual boot configuration and things went well.  I did not however, back up windows 7, as it was a fresh install and I did not realize Linux would do away with the windows boot commands.  My idea now is to back the lap top hard drive up to a desktop running windows 7.  

My thinking is I can then overwrite the disk on the lap top with whatever version of Linux I want, and then down the road if I want windows 7 back on the lap top I can reinstall it and deal with the boot up issue then.

Would this be the best way to handle wanting to preserve what is on the lap top and still be able to play soley with Linux on this machine or is there a better way?  And can anyone recommend a program that will make a bit for bit (not sure if this is the correct term) copy of the lap top drive to the desk top machine. I have the two machines on the same network while in Windows mode.  

As always I am new to this so if someone has a better idea or I have used some incorrect terminology let me know.

Chris

---

### Post by Perfect Storm on 2012-01-01
Moved to Other OS/Distro Talk.

---

### Post by Frogs Hair on 2012-01-01
You can clone a hard-drive with the software at the link . I am not familiar with preinstalled windows if that is what you have .  You should be able to restore the windows boot option by updating grub as long as you didn't  overwrite it with Mint  . Oem copies of Windows preinstalled or other wise can only be used on the computer they are first installed on . [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by oldfred on 2012-01-01
A couple of more choices. I have not used either, but they say these work. But Windows has to be in the same NTFS partition and may need repairs, so having a repairCD or USB makes sense.

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by chris1216 on 2012-01-01
Frogs and Old Fred,

Thank you both.  The links were informative.  What I ended up doing was using a system recovery cd and the gparted function to get rid of the partitions associated with Mint.  I then was able to get my hands on a windows 7 recovery cd, and that took care of the boot loader options.

Later today I will back it up to the hard drive on my desktop.  My issue now is I cannot figure out how to make the entire C drive on the lap top visible on my home network.  In reading different threads it seems this is the way windows has it set up as I am not the only one to express frustration over it.  I cannot get the folders that show windows startup and system functions to be visible.  If you have any advice on this let me know.  

Chris

---


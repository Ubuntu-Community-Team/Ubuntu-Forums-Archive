---
title: "Particular mount/boot situation?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by drdrewusaf on 2006-06-26
Hello, 

First, I am new to the forum and brand new to Ubuntu.  I have used Solaris only a little bit, so my Linux experience isn't nil, but it ain't much either.

I have been all over the web looking for an already answered post of someone in a situation close to mine.  To no avail, no one in a situation close to mine had gotten any answers.  So here it is...  A while back I installed Fedora onto a second partition on my RAID 0 array on an HPT374 controller.  Fedora would not boot, something with the RAID, but Windows XP still would using Grub.

Recently, I got off my butt and tossed another HD into my computer.  Thinking that I should have no problem w/ Linux booting now, I looked around and decided that Ubuntu would be a better choice for me.  So here is what I have:

2 x 30GB HD's in RAID 0 on the HPT374, 1 partition, ntfs, winxp
1 x 120GB HD alone on the first IDE channel, 3 partitions: root, swap, fat32

The problem is that the Windows NTLDR cannot boot between devices on different controllers.  It's theoretical, but it doesn't work for me.  Grub, on the other hand can.  I have tried EVERY configuration I have seen on the net to get Grub to boot to the RAID array.  Grub's device map is as follows:

(hd0)	/dev/hda
(hd1)	/dev/hde
(hd2)	/dev/hdg

Where hde and hdg are the RAID array represented as two drives.  Here is my menu.lst (edited to just show my test Windows entries):

title		Windows XP (no map)
rootnoverifiy	(hd1,0)
makeactive
chainloader	+1

title		Windows XP (map)
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverifiy	(hd0,0)
makeactive
chainloader	+1

title		Windows XP (no map boot)
rootnoverifiy	(hd1,0)
makeactive
chainloader	+1
boot

title		Windows XP (map boot)
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverifiy	(hd0,0)
makeactive
chainloader	+1
boot

All give me the same error: 

Error 13: Invalid or usupported executable format. 

I'm assuming that the problem is that the drives aren't listed as one device.  So, I looked for info on how to get the two drives to look like one to Ubuntu and Grub.  I've tried to assemble the array using mdadm, but it says there is no superblock.  I am reluctant to force it because I have no idea what the implications are.  The mkraid command is not available, why, I don't know...it's not listed in the synaptic manager.

I'm stuck.  I couldn't even get the drive to mount until yesterday when I got dmraid installed so I could at least access the drive.  However, the array still listed as two devices in /dev/mapper:  hpt37x_baffifcchb and hpt37x_baffifcchb1.  Should I add the /dev/mapper items to the device.map in  for Grub?  Which one should I point Grub at in menu.lst?  Is there a way to make Ubuntu and thus Grub see them as one device/drive?

ANY help is welcomed!  Thanks!


Drew

---

### Post by drdrewusaf on 2006-06-26
Bueller?  Bueller?

---

### Post by jrd on 2006-06-26
Not sure if this is what you need. I don't know much about raid.
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

### Post by drdrewusaf on 2006-06-28
Well, I figured out a work around, and while not as clean as I would like, it works and that is all that matters. :D

I downloaded and installed wingrub [here.]("http://grub4dos.sourceforge.net/")  Wingrub gives you the ability to install and load Grub on a Windows partition w/o actually changing the MBR.  Instead of messing w/ the MBR, if you decide to configure it in this way, it will load Grub via the NTLDR's boot.ini file.  It's not exactly user friendly but it was easy enough.  Thanks for the help!

If anyone is in a similar situation and needs help, send a PM my way.



Drew

---


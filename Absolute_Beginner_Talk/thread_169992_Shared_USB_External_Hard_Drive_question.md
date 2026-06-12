---
title: "Shared USB External Hard Drive question"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-05-03
I have a 250 gig Lacie External USB Hard Drive.  I need to be able to use it as sort of a gas station to gas up coworkers with new versions of VMWare workstation images we've created.  These coworkers are all Windows XP folks. 

However, I also still want to plug it into my Ubuntu laptop when it's not travelling around the company with me and use it with both read/write.  I should clarify, this drive is purely a file dump - not a dual boot XP or dual partioned NTFS/Ext3.  Just one drive. And the goal: one partition.

**Requirement #1**: I need read/write on the Windows side.  And without having to install extra drivers either.  I need to show up, plug it in, and be ready to go.

And **requirement #2**: I need read/write on the Ubuntu side.

From everything I've read, Vfat / Fat32 is the only file system that will work for me.  But when I format the drive Fat32 from the Ubuntu side and try to plug it in to a Windows XP box, the Drive Manager sees the drive but it does not get mounted and is inaccessible.

If I try the reverse and try to format it from Windows XP ( *format /FS:Fat32 /V:Diskshare /Q* ) Windows tells me the volume is too big for Fat32.

Does anyone have a suggestion on how I might handle this?  I have a 1 Gig thumb drive that works fine in this regard -- I can move it from Windows to Ubuntu seemlessly and have both read and write.   But it's only 1 gib and this drive is 250gib.

Thanks in Advance,

Craig

---

### Post by yager on 2006-05-03
Try this link.

[https://bcrc.bio.umass.edu/phpwiki/index.php/CreateLargeFat32Partitions?PHPSESSID=d5e34480b5db7a186240b42dcdbc080c](https://bcrc.bio.umass.edu/phpwiki/index.php/CreateLargeFat32Partitions?PHPSESSID=d5e34480b5db7a186240b42dcdbc080c)

This author seemed to figure out how to get a 97G FAT32 partition that XP would work with.

---

### Post by macdo on 2006-05-03
Windows doesn't like USB partitions larger than 32GiB in Fat32...

You could try [this]("http://www.ramelectronics.net/html/usb_hard-drive.html#install"), however - it seems to say that you can format larger drives as Fat32. YMMV...

---

### Post by yager on 2006-05-03
[QUOTE=macdo]Windows doesn't like USB partitions larger than 32GiB in Fat32...
[/QUOTE]
Here is a link to a company, [Ridgecrop](http://www.ridgecrop.demon.co.uk/index.htm?fat32format.htm), that has written a custom formatter to handle oversized drives with FAT32.  I would say you should give this a shot as it formats from Windows XP and after running, Windows XP can read and write to the drive.  The author even gives instructions specific to USB and firewire drives as well so it implies there are no limitations to external drives.

---

### Post by mybootorg on 2006-05-05
Thanks guys!  Ridgecrop did the trick!  I tried the Win98 boot disk and Fdisk route but had problems creating the diskette.  Who uses floppies anymore.

I really appreciate the help. Have a great weekend!

---

### Post by jeremy on 2006-05-05
I stuck a 120GB IDE drive into a Ext USB box (safecom SUSB2-35CAF), plugged it into my (then) Hoary PC, and formatted it as FAT32 (one 120GB partition). It works perfectly, now using Breezy, and have connected it to both windos xp, and Mac 10.

---


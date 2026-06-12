---
title: "Not recognizing DVDRW on install"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by craigp on 2006-01-20
Hey i am really getting frustrated and i dont know what to do anymore...I am not a novice linux user but advanced windows user.. I am trying to install ubuntu 5.10 on my system and it wont detect the cd-rom so i have to continue to exit my installation. My drive is a Sony DVDRW DW-D22a. It works fine in windows. I have have read a few other people's complains with this issue and i believe it has something to do with my hard drive being sata and my dvdrw being ide. I have tried changing the settings for handling this in my bios..auto and combination do not work and with it set to enhanced it wont even detect the drive in windows. Anyone have any ideas? I tried looking for a driver download for it to put on a floppy but no go....Thanks

---

### Post by craigp on 2006-01-20
i have it set in the bios to boot from the drive but for some reason it still wont with any disks..so i am using a floppy boot disk to let me select to boot from the cdrom so that might be playing a role...anyone able to help I want to get linux on so i can dual boot instead of just being stuck with windows:cry:

---

### Post by ajgreeny on 2006-01-20
Try a copy of Smartboot Manager and copying it to a floppy if you have one on your machine using dd in linux or rawrite in windows.  Boot from the floppy and that may then allow you to boot from your CD/DVD drive.

---

### Post by craigp on 2006-01-20
i downloaded the smart boot floppy and that would allow me to boot to the disk but then ubuntu wouldn't recognize the driver for the drive....

but i ended up getting it working..it was a setting in the bios that said disable ide pci something...for some reason even with it disabled windows was detecting it and i could use it..but i enabled it and i could then boot off my cdrom again...

---


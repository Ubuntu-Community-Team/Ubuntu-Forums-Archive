---
title: "Karmik not booting on native 10.6"
date: 2009-12-08
forum: Apple Hardware Users
---

### Post by tobias81 on 2009-12-08
Hi everybody,

    I've been probably trying all possibilities but to no avail. I have a new macbook pro 13" 5,5 that came natively with snow leopart (10.6) (so GUID partition table) and I'm trying to get it to dual-boot ubuntu 9.10.

so this is what I've tried:

- in mac OSX with bootcamp created a partition for ubuntu
- tried with and without rEFIt result is about the same
- installed ubuntu 9.10 
     - tried both installing GRUB into the MBR as well as /dev/sda3 (
     - tried leaving the OSX created partition untouched just formatting it with ext4 (since it leaves like 128 MB free space gap between the OSX partition and the windows partition - don't know if that is needed or not ... anyway

- installation works fine - no errors or anything
- after reboot, OSX still works fine
- booting Linux
   -> with rEFIt when I try to boot linux nothing - just sits there
   -> with OSX native bootmanager (just holding down option key and choosing the windows partition) I get GRUB on the screen, but that's it, no error, nothing, again just sitting there


any ideas??
 ... I really can't stand OSX anymore, don't know why everybody is talking so good about it (well I guess it's better than windows) however I need a working Computer for work and I don't have time to get Ubuntu all setup in one sweep ;/ so I need it to dualboot - at least for a little while

---

### Post by linuxopjemac on 2009-12-08
did you follow this ?
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic)

---

### Post by tobias81 on 2009-12-08
thanks for the answer but well I know this how to but it just tells you how to get the details working... I never even get to start ubuntu up. 
however I followed another how-to (sorry forgot the exact link) that tells you how to use it with rEFIt etc etc ... but it didn't work
all of these howtos that I found are based for non native Snow leopard macs... and Snow leopard is the first that started to ship with a GUID partition table - so they say at least (never owned a mac before) ... and it very much looks like the GUID is my problem. because seeing only GRUB should mean that grub can't find stage 2 / /boot partition
so I never dealt with GUID tables before so I don't really have an idea how to fix this ... and unfortunately I found only helps on how to do this if you re-install everything - which I don't wanna do for now

---

### Post by linuxopjemac on 2009-12-08
Try to read and understand this one:
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

Please report us if you succeed how you did it.

---

### Post by tobias81 on 2009-12-08
thanks.. yeah that looks more like it would contain the answer for me ... it's pretty long so it'll take me a little to dig through it (probably weekend ;/) but yeah I'll report back if I get it to work somehow

---

### Post by linuxopjemac on 2009-12-08
[http://forums.fedoraforum.org/showthread.php?t=103636](http://forums.fedoraforum.org/showthread.php?t=103636)

---

### Post by tobias81 on 2009-12-11
ok ... I tried this last howto (for FC5) but for me the MBR and GPT table are always in sync (according to this partition tool of rEFIt) and I basically get never asked to sync those 2 ... so rEFIt always just shows my the Microsoft symbol as a second option to OSX and even if I choose that it'll just hang ...
without rEFIt I always get the same issue - GRUB... and hangs after. I tried to install "grub-install / grub-setup" with pretty much every option combination I could think of ... but the best I could get out of it was an error/warning saying that this is a GUID system but it can't find the partition with the bootup info (i forgot the exact wording, but I'll post that too within the next couple of days) - it will do it anyway by forcing - but that obviously is not doing any good

thanks all for your help

---


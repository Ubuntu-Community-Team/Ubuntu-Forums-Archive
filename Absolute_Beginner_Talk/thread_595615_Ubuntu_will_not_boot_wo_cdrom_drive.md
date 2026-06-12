---
title: "Ubuntu will not boot w/o cdrom drive"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mrwelch on 2007-10-28
When I installed Ubuntu I used my cdrom drive. I have all the software I need installed and need to physically remove the cdrom from my system. the problem is that Ubuntu fails to boot when it is disconnected.

I plan on installing a USB cdrom later but need to disable the main cdrom drive so I can put the cover back on my case. My main hd and my other two hd's on raid1 take up my drivebays in drive caddies.

I understand that there are ways to install Ubuntu without a cdrom drive but I'm hopeing not to have to start over. When I boot without the cd attached all I get is busybox prompt coming up.

Any help in accomplishing this would be appreciated

TIA

Michael

---

### Post by Clay_Banger on 2007-10-31
try this, boot up with the cdrom attached.
open up the terminal and type in:
```
sudo nano /etc/fstab
```
and put a '#' (without the quotes) infront of the line that reads similar to:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
so it becomes:
```
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
then ctrl+x, y, [enter]

shut down your comp, remove the cd drive, and see if it boots.

---


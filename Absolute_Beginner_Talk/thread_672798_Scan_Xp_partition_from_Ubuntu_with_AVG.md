---
title: "Scan Xp partition from Ubuntu with AVG"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by achusonline on 2008-01-20
My problem is like this,

I have ubuntu and XP installed.
I have downloaded AVG for ubuntu.
I want to scan my XP partition for viruses from ubuntu using AVG.

Is it possible, could someone possibly tell me how?

---

### Post by jeffus_il on 2008-01-20
Yes it is possible, just need a mounted, writable ntfs/fat partition, run avg and point it at the right folder. I did it a while back so I don't remember details, post if you need more details.

---

### Post by achusonline on 2008-01-20
i need more details like the command

i used avgscan /sda1 bcoz sda1 is my xp partition but not working....can u giv the exact command pls?

---

### Post by achusonline on 2008-01-20
ok i figured it out...
just like u said, had to find the right path to the folder
in my case i found it was like,
avgscan /media/sda1 with sda1 being my parition where xp was installed

so avg is running and it has found something like obfustat virus....

thanks for the help bro c ya

---

### Post by sandysandy on 2008-01-20
are u able to remove windows virus in win XP when doing scan with AVG from Linux.

regards

---

### Post by jeffus_il on 2008-01-20
Yes, you can and more easily, since the windows files are not running and not locked.

---

### Post by sandysandy on 2008-01-20
> **jeffus_il said:**
> Yes, you can and more easily, since the windows files are not running and not locked.

thanks

---

### Post by bryncoles on 2008-01-24
achusonline (or anyone for that matter) -would you mind posting how you found the correct file path for scanning the windows partition? im having a little trouble working that bit out. 

thanking you in advance!

---

### Post by barbedsaber on 2008-01-24
and when you have done that, could ypu pleas mark this thread as solved, see my sig for details.

---

### Post by bryncoles on 2008-01-25
i figured it out last night! mount the drive as normal so it appears on your desktop, right click it, select properties, select volume at it'll give you the address of the drive there. then just type that into avg's top line and it'll mount the drive in avg, ready for scanning! yay!

---

### Post by Drakkor on 2008-01-25
Interesting thread , could this also be done from a live Ubunutu disc ? :)

---

### Post by Nhatz on 2008-01-25
First update AVG.....
sudo avgupdate -o

then....

sudo avgscan -clean /media/LOCATION_OF_THE_MOUNTED_DRIVE
this should do the trick....... (and clen/heal the detected virus)

:guitar:

---


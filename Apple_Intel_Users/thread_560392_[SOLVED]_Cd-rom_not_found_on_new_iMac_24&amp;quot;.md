---
title: "[SOLVED] Cd-rom not found on new iMac 24&amp;quot;"
date: 2007-09-26
forum: Apple Intel Users
---

### Post by micheleo on 2007-09-26
Hi everyone. 

I just installed Ubuntu 7.04 64 on a brand new iMac 24".
The system works fine but the cdrom is not found, no device is created under /dev.

In /etc/fstab there's this line:
```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
but /dev/hda does not exists. 

Any idea? 
If you need dmesg or anything else just ask ;)

Thanks in advance

M.

---

### Post by pxwpxw on 2007-09-26
That will happen if there is no CD in the drive.

---

### Post by micheleo on 2007-09-27
It would be too simple! ;)
If I insert the cdrom nothing appens, no messages on dmesg. 
Moreover I can't eject the cdrom anymore... :lolflag:

---

### Post by pxwpxw on 2007-09-27
Yes, thought it was too easy. I don't have an iMac, cant really help much.
I suppose it  must work for macosx and you can eject from there, so the problem is with ubuntu 704 software.

Well, I just checked here, and on my G5
/dev/hda is my cdrom 

but on my MacBook
/dev/scd0 is the cdrom

So maybe have a look in /dev/ for scd0?

---

### Post by micheleo on 2007-09-27
no such dev.. :(
thank you anyway! :)

---

### Post by newman on 2007-09-27
I'm still trying to understand why anyone would install Linux on a new Mac which already has a superior OS!

---

### Post by alephsmith on 2007-09-27
You have to load the piix module in Feisty to use the disc drive on a Santa Rosa MBP. Could it be the same thing?

---

### Post by cyberdork33 on 2007-09-27
> **alephsmith said:**
> You have to load the piix module in Feisty to use the disc drive on a Santa Rosa MBP. Could it be the same thing?worth a try.

---

### Post by cyberdork33 on 2007-09-27
> **newman said:**
> I'm still trying to understand why anyone would install Linux on a new Mac which already has a superior OS!
Thanks for your comment.

---

### Post by micheleo on 2007-09-28
sudo modprobe piix
and adding module in /etc/modules did the trick!
thank you very much guys! :popcorn:

---


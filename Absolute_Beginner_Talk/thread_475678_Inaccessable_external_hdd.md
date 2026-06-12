---
title: "Inaccessable external hdd"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Tuning_In on 2007-06-16
Hi!

I'm having problems accessing my external hdd. The messages I get when I'm trying to access are: Cannot go to file:///media/My-disk. You don't have accessright to this....When I use the gksudo nautilus command and so on to change the permissions I get the message:The owner could not be changed.Couldn't change the owner of "My-disk" because it is on a read-only disk.I I've install the ntfs-3g and the config package. 

I've tried to mount it on /media/My-disk, Is this the right way to do it? 
Running:
sudo fdisk -l 
df -h

I get this output:
Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30401   244196001    7  HPFS/NTFS

Being a noob I dont know if I have done it right?
I dont know where to begin to get accsess!

Thanks in advance:)

---

### Post by ugm6hr on 2007-06-16
I'm no expert, but thought I'd point you towards some help:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Hopefully, what you've done so far should look something like that - just substitute "dev/hda1" for "dev/sdf1" and "/windows" for "/media/My-disk"

Also, having installed ntfs-config - have you run it?  You should do this after the above.

Out of interest - I'm assuming this is a USB HD - which should have been auto-mounted the first time you plugged it in.  Where was it mounted to?  You may have to unmount it from there if it's not /media/My-disk.  

Also - does gksudo nautilus give you access to the files on the drive?  And does it give write access?  The answers to these questions may well give a clue as to how far you've gotten in the process.

---

### Post by Tuning_In on 2007-06-16
Hi

I don't really know how I did it, but I managed to get access. I did unmount it and changed  some preferences in the modify-section setting it up again. 

Thanks for tip anyways:)

---


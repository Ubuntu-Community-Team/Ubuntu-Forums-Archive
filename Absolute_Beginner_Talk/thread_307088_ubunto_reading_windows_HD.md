---
title: "ubunto reading windows HD"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by yoav200 on 2006-11-26
Hi all,

I have install Ubuntu 6.10 on an old PC I have.
the thing is I have 2 hard drives on that PC, dooring installation
one was formatted and Ubuntu was installed on it successfully.

The second one still have data but it is with FAT 32 file system.

When I go to device manager it looks like Ubuntu recognize that drive but when I go to places I can't seem to find it.

Can I browse the content of that HD with Ubuntu OS ?

---

### Post by Gannin on 2006-11-26
When you say you tried going to Places, did you try going to Places > Computer?

---

### Post by kelbizzle on 2006-11-26
You should be able to mount the drive on boot by following these instructions...

Make a new folder or directory
```
sudo mkdir /media/windows
```

Backup your fstab (good practice)
```
sudo cp /etc/fstab /etc/fstab_backup
```

Open up the orginal fstab in gedit
```
gksudo gedit /etc/fstab
```

Assuming the locations of the partion is /dev/hdb1
Add this line to the end of it
```
/dev/hdb1    /media/windows vfat  iocharset=utf8,umask=000  0    0
```

Save the file.
Then remount /etc/fstab without rebooting
```
sudo mount -a
``````

```

---

### Post by yoav200 on 2006-11-27
yes i did 
but all i see there is system files, floppy.

is the second hard disk should be there as an Icon ?

---

### Post by yoav200 on 2006-11-27
kelbizzle,

I didn't quit understand what you showed me.
I'm not talking about a partition, it is a phisical hard disk.
the thing is, i have another computer connected to this one (through hub) and i can see all the shared folders on that computer (it is Windows xp). so basecly if Ubuntu recognize the shared on the XP comp it should have no truble with the second Hard Disk...

---

### Post by yoav200 on 2006-11-27
Hi kelbizzle,

I did exactly what you wrote me to do....

     AND IT WORKED !!!

I can now see all the HD content under /media/windows it's great

thanks alot :p 

cheers
Yoav

---

### Post by kelbizzle on 2006-11-28
Your welcome. Glad I could help. Maybe in the future you see someone else having the problem you help em out?:-D

---


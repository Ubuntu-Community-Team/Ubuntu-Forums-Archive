---
title: "mount: special device /dev/hdc does not exist"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-23
I am trying to use the 'drivers' cd that came with my laptop to get the right ****ing driver for ndiswrapper, but get the above message when trying to mount her....
 What other two day headache do I need to get into?

Please tell me there is an apt-get for this...

---

### Post by Kurt` on 2006-03-23
/dev/hdc would be your "secondary master" hard disk.

If you're trying to mount a cd-rom, try:

mount -t auto /dev/cdrom0 /media/cdrom0

---

### Post by Papa-san on 2006-03-23
```
john@laptop:~$ mount -t auto /dev/cdrom0 /media/cdrom0
mount: only root can do that
john@laptop:~$ sudo mount -t auto /dev/cdrom0 /media/cdrom0
mount: you must specify the filesystem type

```

---

### Post by joshuapurcell on 2006-03-23
If you are trying to mount a CD, you should be able to just put the CD in the drive and do this command:```
sudo mount /dev/cdrom
```Usually this would work since your **/etc/fstab** would have an already existing entry for your CD drive (called cdrom). What do you get when giving this command? If you are still getting errors, then please post your **/etc/fstab** file.

---

### Post by Papa-san on 2006-03-23
I left the cd in the drive when i shut down last night, and when I booted this morning it was mounted...
However the 'archive manager' cannot open it. I get the error:

Archive type not supported...

---

### Post by LordBug on 2006-03-23
Couple of things:

/dev/hd? devices aren't mountable.  /dev/hd?X devices are (e.g. /dev/hdc1).

For CDROM drives, unless there's a special reason not to, I always set the type to iso9660.  So 'sudo mount -t iso9660 /dev/hdc1 /media/cdrom' would work (this is assuming that /dev/hdc is a CDROM drive).  /dev/cdrom as mentioned above is a symlink to the /dev/hd?X device.

As for the CD being unreadable on an automount, I have this happen from time to time.  I just unmount (sudo umount /media/cdrom) and re-mount manually.

---

### Post by Papa-san on 2006-03-23
Now I have it mountable and unmountable. Now I have to find a way to extract my wireless drivers off of it...

](*,) <--- My most used smilie!

I apologize for my years of Windows ignorance, and just wish I would have started using this OS (linux anyways) years ago...

I have learned so much in the last three weeks that it is scary, but the application in regards to this issue doesn't show it...

---


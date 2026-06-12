---
title: "fat permissions &amp; mounting"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by shadowfist on 2006-03-01
(all of this is in KDE I havent tried it in Gnome yet)

I am trying to mount my fat partition and I can get it to mount and I can access the files. but I am having a strange problem.

when I use konquer (spelling?) and browse the fat volume it tells me that I have RWXD etc... I think only two spots are not marked in the permission box (owner?). 
when I am in for example firefox i can save files to these folders no problem, but I cannot create folders from firefox. it tells me that I dont have the permissions for that. and if I try to COPY a file to the folder from say, the desktop it tells me that I dont have the permissions as well.

now here is my problem I want to somehow affect the mounting permissions I am assuming but I dont want the drives to automaticaly mount every boot up. I want to be able to monut them by hand when I want access / to save files.

thanks a bunch \\:D/

---

### Post by knalle on 2006-03-01
how do you mount your fat partition? mount has MANY parameters for controlling the mount of vfat

---

### Post by shadowfist on 2006-03-01
I just type "mount /dev/hda1 /windows"

that is it. it seems to get the right permissions, but something is not quite right.

---

### Post by LordBug on 2006-03-01
I suggest using the umask option when mounting FAT partitions.  Change your mount to this:

"mount -t vfat -o umask=0000 /dev/hda1 /windows"

You can read the mount manpage for how to use umask, but this should give you all rights to the mountpoint.

---

### Post by shadowfist on 2006-03-01
sounds good I will give that a try.

and by the way what do the "-t" and "-o" switches do?

---

### Post by Jucato on 2006-03-01
-t means to mount a specific **t**ype (filesystem), and -o is for **o**ptions

---

### Post by shadowfist on 2006-03-01
ahhhh, thanks for the clarification... I wasnt thinking :rolleyes:

---

### Post by tadashi on 2006-03-01
You can just use mount <dev> if you have it defined in the fstab already (options, type, and mount point).

/dev/hda1  /windows  vfat  umask=000  0 0

Then you only have to type: mount /dev/hda1

---

### Post by Jucato on 2006-03-01
It might be even preferable to have it in fstab so that it mounts on boot, especially if you find yourself using that partition often. The only partitions that I don't put in fstab are the ones I very rarely work with (read: NTFS)

---

### Post by shadowfist on 2006-03-01
how do you specify in fstab for a device to mount or not mount automaticaly?

---

### Post by Jucato on 2006-03-01
If it's in fstab, it's mounted on boot (I think). I think one of the options should be "default"? I'm not entirely sure, though.

---

### Post by aysiu on 2006-03-01
If you have it in the /etc/fstab, it'll mount automatically on boot.

You don't want *defaults* to be in your /etc/fstab line for a FAT partition, though, as you won't be able to have read/write permissions to it.

For a step-by-step:
[http://www.psychocats.net/linux/mountwindows](http://www.psychocats.net/linux/mountwindows)

For a quick-and-dirty:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by Sutekh on 2006-03-01
[QUOTE=shadowfist]how do you specify in fstab for a device to mount or not mount automaticaly?[/QUOTE]Use **auto** and **noauto**

Edit: An example
```
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222,**auto** 0 0

/dev/hdc /media/cdrom0 udf,iso9660 user,**noauto** 0 0
```

---

### Post by shadowfist on 2006-03-01
[QUOTE=Sutekh]Use **auto** and **noauto**

Edit: An example
```
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222,**auto** 0 0

/dev/hdc /media/cdrom0 udf,iso9660 user,**noauto** 0 0
```[/QUOTE]



OOOOOoooohh, thank you very much. you have made me quite happy\\:D/

---


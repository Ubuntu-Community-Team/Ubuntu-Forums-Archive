---
title: "[SOLVED] Some files show up, but others don't!"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by edarroyo on 2007-08-31
Hello, I am trying to fix a problem here, but can't seem to find any pattern. I mounted a 20 GB partition to my home folder. The format is NTFS and it mostly holds files that I share between the two OSs that I run, which are Ubuntu 7.04 and Windows XP Pro. For some strange reason Ubuntu does not detect some music files, in mp3 format, but Windows does. It's around 300 mp3 files. I used ntfs-3g to mount the partition. Ihope somebody could help. Thanx!
Edgardo

---

### Post by diatribe on 2007-08-31
if the directory or any of the files start with a . they will be considered hidden under linux, try using the view hiddenf iles option in your file browser and see if it locates them

---

### Post by edarroyo on 2007-08-31
No, they are music files, i can see them in Windows, but not in Ubuntu :(

---

### Post by diatribe on 2007-08-31
I am saying if the name of the file is .iamanmp3.mp3 it will show as hidden

---

### Post by edarroyo on 2007-08-31
No, it doesn't start with a . (dot) at all. I'll give you some examples of the names:
Si Me Adverti.mp3
Toca Mi Cancion.mp3
Que Mas Da.mp3
And so on...

So, to check what the hell was going on, I copy all the files that I could see in WIndows, but not in Ubuntu on the a Flash Drive. Then, I boot up Ubuntu and tried copying those files into the same folder that they are in in Windows, but I would get a "generic error" pop up.

---

### Post by jordanmthomas on 2007-08-31
Try adding ```
locale=en_US.utf8
``` (or whatever your locale is) to your mount options.  Chances are, whatever locale you're using now doesn't support certain characters.

A line from my fstab so mine work right:
```
/dev/disk/by-label/external	/media/external	ntfs-3g	users,user,locale=en_US.utf8,force 0 0
```

It's removable, but gnome-mount looks in fstab for it so it knows how to mount it right.

*edit*  and yes, for some reason I had to put both user and users so the permissions would work right.

---

### Post by bashologist on 2007-08-31
Maybe your're looking in a different folder? Try using find.
```
find /windows -name "Que Mas Da.mp3"
```

---

### Post by edarroyo on 2007-08-31
> **jordanmthomas said:**
> Try adding ```
locale=en_US.utf8
``` (or whatever your locale is) to your mount options.  Chances are, whatever locale you're using now doesn't support certain characters.

A line from my fstab so mine work right:
```
/dev/disk/by-label/external	/media/external	ntfs-3g	users,user,locale=en_US.utf8,force 0 0
```

It's removable, but gnome-mount looks in fstab for it so it knows how to mount it right.

*edit*  and yes, for some reason I had to put both user and users so the permissions would work right.
 

THANX! I just added the locale and it worked :D thanx a lot! now everything is perfect! i'm ditching windows for sure :D... thanx again!

---


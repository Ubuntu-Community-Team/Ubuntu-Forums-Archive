---
title: "Read permission for a mounted NTFS drive?"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by cafevincent on 2005-12-09
How to give read permissions for a already mounted NTFS drive? I tried sudo chown vincent /media/120gb but it gives error 'read-only file system'.

---

### Post by frodon on 2005-12-09
Could you explain a little bit more what is your problem and what you want to do ?
It could also be interesting to post your fstab file : ```
sudo gedit /etc/fstab
```

---

### Post by cafevincent on 2005-12-09
[QUOTE=frodon]Could you explain a little bit more what is your problem and what you want to do ?
It could also be interesting to post your fstab file : ```
sudo gedit /etc/fstab
```[/QUOTE]

I don't see how I can put it any clearer than that. I'm trying to read the content of a hard drive that has NTFS file system and is already mounted. I can't copy content, I can only browse. I can't apply permissions because they are grayed out. I can't add ownership because the drive is read-only filesystem.

```
/dev/hdd1	/media/120gb	ntfs	users,defaults,dmask=222,fmask=333,nls=utf8 0 0
```

---

### Post by aysiu on 2005-12-09
```
sudo umount /media/120gb
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace this line: ```
/dev/hdd1	/media/120gb	ntfs	users,defaults,dmask=222,fmask=333,nls=utf8 0 0
``` with this one ```
/dev/hdd1	/media/120gb	ntfs	nls=utf8,umask=0222 0 0
``` Control-X, y, Enter. ```
sudo mount -a
```

---

### Post by frodon on 2005-12-09
By the way, i'm not sure that NTFS supports unix rights and ownership.

---

### Post by cafevincent on 2005-12-09
[QUOTE=aysiu]Replace this line: ```
/dev/hdd1	/media/120gb	ntfs	users,defaults,dmask=222,fmask=333,nls=utf8 0 0
``` with this one ```
/dev/hdd1	/media/120gb	ntfs	nls=utf8,umask=0222 0 0
```[/QUOTE]

No help. Still says ```
chown: changing ownership of `/media/233gb1': Read-only file system
```

[QUOTE=frodon]By the way, i'm not sure that NTFS supports unix rights and ownership.[/QUOTE]

Well I did have a drive working like that when I originally installed ubuntu but I can't remember what I did anymore. I don't know if the trick was to change ownership or what but the point is its possible to read from NTFS drive and I need to know how.

---

### Post by aysiu on 2005-12-09
[QUOTE=frodon]By the way, i'm not sure that NTFS supports unix rights and ownership.[/QUOTE] You can't chown it once it's mounted, but you can mount it with the correct permissions.

---

### Post by BLTicklemonster on 2005-12-09
The way I read it when I was trying to mount my ntfs was that it will not be anything but read only. You have to have a fat32 partition to use as an intermediary or something like that. I wish I'd paid more attention now, as it seems there were instructions on exactly what to do.

---

### Post by cafevincent on 2005-12-09
[QUOTE=aysiu]You can't chown it once it's mounted, but you can mount it with the correct permissions.[/QUOTE]

That sounds good, how do I do that?

---

### Post by BLTicklemonster on 2005-12-09
[http://ubuntuforums.org/showthread.php?t=71967](http://ubuntuforums.org/showthread.php?t=71967)

some ideas in here

---

### Post by cafevincent on 2005-12-09
[QUOTE=cafevincent]That sounds good, how do I do that?[/QUOTE]

Never mind, it did work but I didn't notice it at first because I was trying with chown.
Thanks aysiu! :smile:

---

### Post by BLTicklemonster on 2005-12-09
Hold on there@!!! what did you do? I'd like to have privvies on my xp ntfs drive I have mounted. (please)

---

### Post by aysiu on 2005-12-09
[QUOTE=BLTicklemonster]Hold on there@!!! what did you do? I'd like to have privvies on my xp ntfs drive I have mounted. (please)[/QUOTE] See [post #6](http://www.ubuntuforums.org/showpost.php?p=558181&postcount=6). It's read-only.

---

### Post by BLTicklemonster on 2005-12-09
Sorry, but 11 made it look like he'd gotten it working.

---


---
title: "Strangeness with file permissions"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-04-07
I have a FAT drive where all my music, video, etc. lives.  It's 777 (read/write by anyone).  Suddenly (as of this morning), when I try to move data around, I am told that I don't have permission on this drive (I can still read on it).  I've tried both as user and root, no dice.  Has anyone encountered this before?  Thx...

---

### Post by taurus on 2006-04-07
What does your /etc/fstab look like now?
```

more /etc/fstab

```

---

### Post by TeeAhr1 on 2006-04-07
It's hdb1.
```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb1 /media/freezer vfat umask=000 0 0
/dev/hda2 /media/windows ntfs umask=000 0 0 user,noauto
```

---

### Post by taurus on 2006-04-07
Two comments.  Try adding another zero (0) after the umask=000 for /dev/hdb1 (umask=0000).  Also, ARE you sure you want to set both read and write to your /dev/hda2, NTFS???  I think it's a good idea to replace the umask with umask=0222 for everybody to read only...

---

### Post by aysiu on 2006-04-07
I noticed you mounted it at /media/freezer

Sometimes the /media and /mnt folders can do weird things.
Try mounting it to a static directory like /freezer

---

### Post by TeeAhr1 on 2006-04-07
Taurus: Negative...  (thanks for the tip on my ntfs partition, though)

aysiu: Trying that, I'll get back in a minute (don't you sleep?)

---

### Post by taurus on 2006-04-07
[QUOTE=TeeAhr1]Taurus: Negative...[/QUOTE]
#-o

---

### Post by aysiu on 2006-04-07
[QUOTE=TeeAhr1]
aysiu: Trying that, I'll get back in a minute (don't you sleep?)[/QUOTE] It's day time where I am.

Let me know how it goes. No guarantees, but it's worth a shot, based on what I've seen.

---

### Post by TeeAhr1 on 2006-04-07
Thanks, aysiu, that did it!  Any idea why that happened?  That's been my mount config since I installed, needless to say I was surprised...

---

### Post by aysiu on 2006-04-07
[QUOTE=TeeAhr1]Thanks, aysiu, that did it!  Any idea why that happened?  That's been my mount config since I installed, needless to say I was surprised...[/QUOTE] I don't know the theory behind it, but I do know /mnt and /media are special folders that are dynamic. gnome-volume-manager and ivman create and remove folders there as USB devices are plugged in.

Static has just always worked for me, and I've seen this problem in other threads, too.

---

### Post by TeeAhr1 on 2006-04-07
One more question, if I may so impose: How do I make the drive show in my "Places" menu?  I assume that automatically looks to /media for entries....

---

### Post by Mustard on 2006-04-07
[QUOTE=TeeAhr1]One more question, if I may so impose: How do I make the drive show in my "Places" menu?  I assume that automatically looks to /media for entries....[/QUOTE]

That's my assumption too, but I have encountered times when it doesnt seem to work (when troubleshooting other peoples problems).  Usually everything I have mounted on a folder inside of /media shows up as an icon on desktop and in the Places menu (on my system at least).

---

### Post by TeeAhr1 on 2006-04-07
In case anyone is searching this thread later: To add a folder or drive to your places menu, select the folder in Nautilus and go to **Bookmarks > Add Bookmark**.  This will also put it in Nautilus's sidebar.

Thx, everyone, for your help!

---

### Post by Mustard on 2006-04-07
[QUOTE=TeeAhr1]In case anyone is searching this thread later: To add a folder or drive to your places menu, select the folder in Nautilus and go to **Bookmarks > Add Bookmark**.  This will also put it in Nautilus's sidebar.

Thx, everyone, for your help![/QUOTE]

Well, there you go.  I've learnt something new. :)  Thanks.

---


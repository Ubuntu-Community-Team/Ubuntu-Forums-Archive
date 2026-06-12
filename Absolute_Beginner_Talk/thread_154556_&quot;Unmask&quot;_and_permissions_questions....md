---
title: "&quot;Unmask&quot; and permissions questions..."
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by Heretic Monkey on 2006-04-03
Everytime i try to copy files from my Windows XP partition over to my ubuntu partition, i always have a lock on the folders by default.  I learned how to do the "chmod" command to give write permissions to a folder and all files/folders inside that folder, but is there anyway to set up the permissions by defualt so i don't have to do that everytime?  I want to be able to copy files/folders from my XP partition to my Ubuntu partition without having to manually reset the permissions.

I've heard about something called "unmask" or "umask" settings, but i don't know where it is, how to get to it, or what to do with it.

BTW: I'm using Breezy Badger 64

---

### Post by Monster_user on 2006-04-03
"umask" is the correct term. It applies a "User" Mask over the directory, when you mount the drive. It should be put in the '/etc/fstab' file,.

**umask 022** Should do the trick, or maybe it should be '0222'? "**nosuid**" also helps.

```
/dev/hda2     /            ext3  defaults                  0     1
/dev/hda1     /media/hda1  ntfs  nosuid,umask=0222         0     0
/dev/hda3     swap         swap  defaults                  0     0
```

The first is a code for the root, Breezy installation. The second is the Windows partition. '/dev/hda1', and '/media/hda1' should point to your Windows partition. However, if you have it installed in a non-standard location, then you will have to make changes accordingly.

---

### Post by Heretic Monkey on 2006-04-03
I tried adding "nosuid" *(umask = 0222 was already there)* to the partition, but when i copy files from the XP to my etc3, the files and folders still show up with limited permissions (and the little red lock in the corner).  Right now, i have:

```
/dev/hda3       /               ext3    defaults,errors=remount-ro       0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,nosuid,umask=0222        0       0
```
Should i take out the "nls=utf8" thing?

---

### Post by carlosqueso on 2006-04-03
Unfortunately, you are gonna have to chmod each time you copy from an ntfs partition, it's just life (don't touch the nls=utf8 thing, it has to do with character sets). I'd suggest copying all the files into the same directory and chmodding it all at once.

---

### Post by Heretic Monkey on 2006-04-03
Crap, saw that coming....

Oh well, i guess it's a minor annoyance i can get used to.  I thought the utf thing had something to do with unicode, but i wasn't sure.  

Well, thanx for the news carlosqueso.

---


---
title: "configuring fstab"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-03-20
hi,
i'm trying to install the ntfs-3g for ubuntu 6.06, after installation I have to edit the fstab with **gksu gedit /etc/fstab**. 

it looks like this:
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

according to the thread i have to mount it like 
/dev/hda1 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0

should it be ?
/dev/hda1       /media/hda1     ntfs-3g   silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda2       /media/hda2     ntfs-3g   silent,umask=0,locale=es_AR.utf8 0 0 
/dev/hda5       /media/hda5     ntfs-3g   silent,umask=0,locale=es_AR.utf8 0 0

or ?
/dev/hda1 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda2 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda5 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0

the es_AR.utf8 0 0 which refers to the codification on what depends?

---

### Post by dbbolton on 2007-03-20
first, make a backup file
```
 sudo cp /etc/fstab /etc/fstab.bak
```then, i think you need to change it to look like this this ```

/dev/hda1 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

i judged by the /dev/hda1 in the line you quoted from the tutorial. i'm not entirely sure what you're trying to do though.

---

### Post by orb9220 on 2007-03-20
> /dev/hda1 /media/hda1 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda2 /media/hda2 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda5 /media/hda5 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0

will put them in default location and show up on the desktop. To do the other

> /dev/hda1 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda2 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda5 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0

You need to make a folder called windows in the /media folder then they will be mounted but will NOT appear on the desktop.

Either way will work it is your choice. The first one is the default and puts icons on the desktop.

---

### Post by raja on 2007-03-20
The second location in each line in fstab indicates the mount point. It has to be different for each partition. Make the mount points first with mkdir and then add the lines in fstab.

---

### Post by Morkhaar on 2007-03-20
well, in theory i am trying to install ntfs-3g to access and manipulate my windows ntfs hdds. (correct me if i'm wrong!)
well i did the 

/dev/hda1 /media/windows ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

drives hda1 and hda5 after restart are mounted, hda5 no but as it is a recovery partition i suppose that has something to do with that. 
i'm still unable to rename/paste etc. though. 
should i remount with sudo mount /dev/hda1?

i already tried the 
/dev/hda1 /media/hda1 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda2 /media/hda2 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/hda5 /media/hda5 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
if the y showed on the desktop would be no problem, as I  had already erased them before, using another command that i dont remember. the problem is that they appeared in the computer, but doubleclicking said 'unable to mount' and mount /dev/hda1 in the terminal said 'already mounted' :-k

---

### Post by rusty4r on 2007-03-20
> It has to be different for each partition.
Yes I don't think you can mount all three partitions to one folder try /media/windows for one and /media/whatever for another and so on

---

### Post by rusty4r on 2007-03-20
maybe the umask should be 000 and not just 0. one 0 for root one 0 for group and one 0 for user

---

### Post by cowlip on 2007-03-20
I'm just curious, have you tried givre's tool called ntfs-config?

It scans for NTFS partitions and mounts them automatically
[http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)
[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970) For Edgy and Feisty

---

### Post by Morkhaar on 2007-03-21
well, no i havent tried it, but i would be willing to. the only problem is that i can't seem to be able to install it. shouldn't the make and sudo make install commands work? could you please tell me what i should be writting after i've been to the directory?

---

### Post by Morkhaar on 2007-03-21
well, thank you all, my drives are mounted and working now !! 
  
 :)

 the only thing is that in 'Computer' appear the icons of the hddrives and are inaccesible. how can i erase them from there?

---

### Post by cowlip on 2007-03-21
I think that's a problem with pmount or something, I remember that happening even in Breezy--some fixes were up at launchpad.  Hopefully it will be fixed in Feisty

---


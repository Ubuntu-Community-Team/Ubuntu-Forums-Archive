---
title: "Accented folders not showing in mounted NTFS partition!"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by rodrigo juarez on 2007-04-18
I can mount my XP's NTFS HDD without any issue doing ```
sudo mount -t ntfs -o umask=0222,nls=utf8 /dev/hda5 /media/windowsxp
``` from the command line. Getting all my documents there, although read-only.
However I'm trying NTFS-3g to get w/r access to it, so I added ```
/dev/hda5 	/media/windowsxp	ntfs-3g	nls=utf8,umask=0222	0	0
``` to fstab and, while it doesn't work (I have no r/w access yet), it doesn't show my accented folders either (my music, my pics and my movies, would be Mi Música, Mis Imágenes and Mis Vídeos in my XP installation in ES_MX)

So I don't know if the issue is with the instruction stated in fstab or with ntfs-3g itself.
Could it be a failed ntfs-3g install?

Any help would be appreciated.

---

### Post by alexlex on 2007-04-18
for read and wright you need to run mount command with -r -w and the umask will be 0000

---

### Post by rodrigo juarez on 2007-04-18
Thanks for your quick reply!
Would that be an addition to fstab or via the command line or both?
And also, the umask set to 0000 would fix de accented folders issue or it just works for the r/w?

Thanks in advance =D

---

### Post by freebird54 on 2007-04-18
Mounting the drive as utf8 is likely to be the cause of the character changes - as I don't think Windows works that way.  (on my system it makes Windows files case sensitive!) What code page (windows style) is Windows using?  Once you know that you/we can google up an answer perhaps...

---

### Post by freebird54 on 2007-04-18
Here is a sample with a locale setting for mounting using ntfs-3g.  You could try that with your locale instead of en_us !


```
/dev/hda3 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

hope it helps

---

### Post by rodrigo juarez on 2007-04-18
Sorry for the delay, I was trying to know the code page from windows and my locale from Ubuntu.
It looks like that's the issue; Ubuntu tells my locale is set to en_US.UTF-8.
doing 'locale -a' I get a list of about 14 entries and none of them seem to be spanish.

---

### Post by rodrigo juarez on 2007-04-18
@ alexlex
As for the r/w access it worked great from fstab, thanks!

---

### Post by rodrigo juarez on 2007-04-18
> **freebird54 said:**
> Here is a sample with a locale setting for mounting using ntfs-3g.  You could try that with your locale instead of en_us !


```
/dev/hda3 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

hope it helps

So it would be like: ```
/dev/hda3 /media/windows ntfs-3g defaults,locale=es_ES.utf8 0 0
```
I guess

---

### Post by rodrigo juarez on 2007-04-18
Nice!
Worked OK. Now I can see my accented files!
I just had to do ```
localedef -i es_ES -f UTF-8 es_ES.UTF-8
``` before your ```
/dev/hda3 /media/windows ntfs-3g defaults,locale=es_ES.utf8 0 0
``` and it was it!
However I used ```
nls=utf8, umask=0000
``` in fstab.

Many thanks =D

---


---
title: "[SOLVED] My DVD drive mounts some discs, but fails on others"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by CCNA_student on 2007-12-16
I am having a very odd problem. My DVD drive, the Memorex 16x, can mount some CD's and DVD's but not others. Discs that can be loaded are:

Ubuntu Installation discs, DVD movies, some audio CD's. 

     Things that fail to mount are:

discs that I burned myself, like mp3 CD's and CD's with my important zip files


     Does anyone know why this would be happening? I have got my DVD writer to read discs, but my DVD-ROM drive keeps saying it cannot mount the device. I have attached a picture of what my DVD-ROM drive says when it gets a disc it cannot read. If anyone need more hardware information just ask. Any help will be much appreciated. 

     Sin Cere,

     CCNA_student

---

### Post by ErusGuleilmus on 2007-12-16
Are the burned discs that wont mount burned in Windows or in (K)ubuntu?

---

### Post by CCNA_student on 2007-12-16
In Windows all of the discs work, they only fail to mount in Kubuntu. My mistake for not mentioning that.

---

### Post by asmoore82 on 2007-12-16
Pure audio CD's do not contain filesystems and thus cannot be "mounted;"
they can only be played with programs such as Sound Juicer (**`sound-juicer`**)
Mixed-mode or "Enhanced" audio CD's can be mouted to retrieve the "extras"

As for the other discs you are having problems with;
**if** the discs are **not** physically damaged (stratches, etc.),
my guess would be that they are either CDs that contain a mini-DVD filesystem(udf)
or DVDs that contain a gigantic CD filesystem(iso9660).
Try mounting them manually in a terminal ...

```
$ sudo mount -t udf /dev/cdrom /media/cdrom
```
-OR-
```
$ sudo mount -t iso9660 /dev/cdrom /media/cdrom
```

If one of these methods works, you may have to manually unmount them before ejecting...

```
$ sudo umount /media/cdrom
```

---

### Post by CCNA_student on 2007-12-16
I tried both commands and the device still does not mount.

---

### Post by CCNA_student on 2007-12-16
That actually worked. I am very grateful for your advice. My drive can now read all discs. Could you tell me why I have to go to the command line to mount a drive though? It is not a real problem, I am just curious as to why. Again, thank you.

   Sin Cere,

   CCNA_student

P.S Visit my blog at [wheatlandlinuxusers.blogspot.com]("http://www.wheatlandlinuxusers.blogspot.com")

---


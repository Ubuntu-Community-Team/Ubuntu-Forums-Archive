---
title: "Writable NTFS"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by ray.rogers on 2006-09-02
Greetings.

I have a mounted NTFS partition {dev/hdb1} which is holding my music.  I want to add to my harddisk, how do I make it writeable?  I do not have a fstab entry for this, i just haven't yet turned off my PC.  It's just mounted.  I would like to make the disk writeable and learn what entry to add to my fstab.

---

### Post by skymt on 2006-09-02
Read/write support for NTFS is still unstable. In other words, don't use it if you want to keep your data. If you're braver than I am (I don't let any beta software mess with my hard drive), try [this HOWTO](http://www.ubuntuforums.org/showthread.php?t=217009).

---

### Post by TFX360 on 2006-09-02
If your new to linux I would think twice!

Be carefull!

---

### Post by macdo on 2006-09-02
Works fine here!

---

### Post by TFX360 on 2006-09-02
I will give it a try then :D

---

### Post by macdo on 2006-09-02
Cool, let us know!
Ave TFX, dati perdant te salutant...

---

### Post by TFX360 on 2006-09-02
> **macdo said:**
> Cool, let us know!
Ave TFX, dati perdant te salutant...


I'm dumbstruck...

It works like a charm!

Edited sources.list
Installed ntfs-3g
Edited /etc/fstab

```
#/dev/sda1    	/media/sda1 	ntfs  		nls=utf8,umask=0222							0	0
#/dev/sdb1    	/media/sdb1 	ntfs  		nls=utf8,umask=0222 							0	0
/dev/sda1	/media/sda1	ntfs-3g		silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other    		0	0
/dev/sdb1	/media/sdb1	ntfs-3g		silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other		0      0
	
```

Rebooted


Copied a few files, tested them, works!


Love it. Thought it was beta-ish, but is more gamma-ish :D


Tnx,

---


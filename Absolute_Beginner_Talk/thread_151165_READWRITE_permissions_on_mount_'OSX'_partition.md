---
title: "READ/WRITE permissions on mount 'OSX' partition"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by phenix on 2006-03-27
Im dual booting macosx and ubuntu..I have successfully mounted the mac partition on ubuntu, but Im unnable to gain read/write access to it...
this is what I have of my fstab file:
/dev/hda3	/mnt/macosx	hfsplus	defaults,umask=ooo	0	0	

I wrote umask=000 thinking that it would grant me the permissions I wanted but nothing so far....
I have checked the spacing and everything seems to be fine, but still nothing happens, 

thank you all in advance!!!!!

---

### Post by aysiu on 2006-03-27
Maybe this might help?
[http://www.ubuntuforums.org/showthread.php?t=149767](http://www.ubuntuforums.org/showthread.php?t=149767)

---

### Post by phenix on 2006-03-28
thanks for for the tip aysiu but thats not really what I needed..my drive mounts already, I just cant gain access to it..I tried using the command umask=000 to see if that would allowe me the access but it didnt.....

---

### Post by aysiu on 2006-03-28
[QUOTE=phenix]thanks for for the tip aysiu but thats not really what I needed..my drive mounts already, I just cant gain access to it..I tried using the command umask=000 to see if that would allowe me the access but it didnt.....[/QUOTE] What about this?

[http://www.jonh.net/lppcfom-serve/cache/567.html](http://www.jonh.net/lppcfom-serve/cache/567.html)

---


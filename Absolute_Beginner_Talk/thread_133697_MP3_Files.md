---
title: "MP3 Files"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-02-20
How exactly can I share my mp3 files from ubuntu and play them in windows?

---

### Post by taurus on 2006-02-20
The best way is to create a partition and format it as vfat (or fat32).  Then, both Ubuntu (or Linux) and Windows can read and write to it.  That's the best way to share stuff between Linux and Windows on a same machine...

---

### Post by vbmaster on 2006-02-20
Well, you can simply create a fat32 partition that, as you might know, is both readable and writable in windows and linux...

It's what I've done in my sistem, a fat32 partition with all my documents, musics, etc.... ;)

**EDIT**: OOoops, too slow.... :P

---

### Post by jasrog on 2006-02-20
I have a fat32 partition how do I get the files on it?

---

### Post by ajgreeny on 2006-02-20
Alternatively get a copy of explore2fs which you can use in windows to explore and export files from linux to your windows OS.  Go to [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) and you should find it there.

---

### Post by user.foo on 2006-02-20
[QUOTE=jasrog]I have a fat32 partition how do I get the files on it?[/QUOTE]

you can (sudo) 

chmod 777 /that_partition

then you could just copy/cut and paste

---

### Post by jasrog on 2006-02-20
that did not work...do I have mount? How?

---

### Post by Coelocanth on 2006-02-20
[QUOTE=jasrog]that did not work...do I have mount? How?[/QUOTE]

Yes, you'll need to mount the FAT32 partition to do anything with it. 

[Read This](http://www.psychocats.net/linux/mountwindows.php). It's a great guide on mounting partitions.

---

### Post by jasrog on 2006-02-20
that did not work...the file system shows windows virtual fat which is /dev/sda5 on my system how can I mount this?

---

### Post by nickle on 2006-02-20
This is not meant to be patronizing, but Ubuntu has wonderful MP3 players,... check them out...

---

### Post by Coelocanth on 2006-02-20
[QUOTE=jasrog]that did not work...the file system shows windows virtual fat which is /dev/sda5 on my system how can I mount this?[/QUOTE]

Did you follow that guide and substitute sda5 everywhere the guide says hdb1?

---


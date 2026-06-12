---
title: "HFS, HFS Plus shenanigans"
date: 2005-08-31
forum: Absolute Beginner Talk
---

### Post by dj_flx on 2005-08-31
OK, maybe I'm just not catching something, but:

felix@cdburner:/$ hmount /dev/fd0
Volume name is "Space Madness\uffff 1.1.6"
Volume was created on Tue Jun 25 17:35:00 1996
Volume was last modified on Wed Aug  3 12:57:36 2005
Volume has 73728 bytes free
felix@cdburner:/$ hcopy :*.* ./home
hcopy: ":*.*": no such file or directory
felix@cdburner:/$ hcopy *.* ./home
hcopy: "initrd.img": no such file or directory

Apparently I'm missing something about the hfs commands/utils. Mounting the floppy drive is about as far as I can get. I can't even get CDs to mount at all.

 ](*,)

---

### Post by poofyhairguy on 2005-09-01
[QUOTE=dj_flx]OK, maybe I'm just not catching something, but:

felix@cdburner:/$ hmount /dev/fd0
Volume name is "Space Madness\uffff 1.1.6"
Volume was created on Tue Jun 25 17:35:00 1996
Volume was last modified on Wed Aug  3 12:57:36 2005
Volume has 73728 bytes free
felix@cdburner:/$ hcopy :*.* ./home
hcopy: ":*.*": no such file or directory
felix@cdburner:/$ hcopy *.* ./home
hcopy: "initrd.img": no such file or directory

Apparently I'm missing something about the hfs commands/utils. Mounting the floppy drive is about as far as I can get. I can't even get CDs to mount at all.

 ](*,)[/QUOTE]

Try 

> gnome-volume-manager

and look in /media/

---

### Post by dj_flx on 2005-09-02
gnome-volume-manager didn't work, but

```
mount -t hfsplus /dev/hdc /mnt/hdc
```

worked when I made a /mnt/hdc directory.  :smile: 

I also got hmount /dev/fd0 to work. I must have been typing something wrong.  :-? 

But in any case, I got the things to mount.

---


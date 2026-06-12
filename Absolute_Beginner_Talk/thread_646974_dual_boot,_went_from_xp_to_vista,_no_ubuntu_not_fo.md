---
title: "dual boot, went from xp to vista, no ubuntu not found"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by docfl on 2007-12-21
Had XP and Ubuntu installed and working fine. Went and put vista on the xp partition and now the Ubuntu instalation not found. If I boot from a live cd I see the partition but cant get a boot loader. Tried the free bcd? and its not seeing Ubuntu either. Ive been looking for somehow to reload grub loader from the live cd but its Im not  making sense out of it.
Gonna keep looking but thought if all else fails I can check back here.
Thanks\
docfl

---

### Post by taurus on 2007-12-21
You need to reinstall GRUB to MBR again.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by docfl on 2007-12-22
I have a live cd but not for the newest version that I have installed.Would a live cd that is about a year old work? or will I need to make a new cd for the version that came out recently?
Thanks
docfl

---

### Post by hyper_ch on 2007-12-22
grub didn't change... that would work.

---

### Post by docfl on 2007-12-22
Ok I gave that a go, tried the section on recovering grub and got this in the terminal:

grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1) #
grub> setup (hd0) #


grub> find /boot/grub/stage1e string



Error 27: Unrecognized command

grub> find /boot/grub/stage1
 (hd0,1)

Im still trying, thanks for the help
docfl

grub>  root (hd0,1) #

grub>  setup (hd0) #

Error 11: Unrecognized device string

grub>

---

### Post by louieb on 2007-12-22
Think your almost there. But why the # at the end of the lines? Don't think they belong.

---

### Post by docfl on 2007-12-22
Ok I finaly got the free bootloader program to work, so Im good to go. 
thanks for the help.
docfl

---


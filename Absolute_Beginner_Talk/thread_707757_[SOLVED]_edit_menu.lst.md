---
title: "[SOLVED] edit menu.lst"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by mist82 on 2008-02-25
I'm trying to change my menu.lst file since when i updated my ubuntu it changed the file. I'm using a live CD to try to make the changes but when i type gksudo gedit media/disk/boot/grub/menu.lst a blank document comes up. however i can access the file through Places/computer/disk/boot/grub/menu.lst but it won't let me save the changes that i have made.  Any ideas out there.

---

### Post by seventhc on 2008-02-25
I think you want to edit this one
```

gksu gedit /boot/grub/menu.lst
```
You can do this while using the live cd.

---

### Post by bodhi.zazen on 2008-02-25
You need a / in front of media

/media/disk/boot/grub/menu.lst

```
gksu gedit /media/disk/boot/grub/menu.lst
```

---

### Post by bodhi.zazen on 2008-02-25
> **seventhc said:**
> I think you want to edit this one
```

gksu gedit /boot/grub/menu.lst
```
You can do this while using the live cd.

nope, you need the path to menu.lst on the HD, which must be mounted somewhere.

---

### Post by seventhc on 2008-02-25
> **bodhi.zazen said:**
> nope, you need the path to menu.lst on the HD, which must be mounted somewhere.
OH, I thought you could still get to it the same way...I was thinking I've edited files that way before...but it must have been while I was in recovery mode..
Sorry for wrong info..:confused:

---

### Post by mist82 on 2008-02-27
thanks guys for your help stupid mistake

---


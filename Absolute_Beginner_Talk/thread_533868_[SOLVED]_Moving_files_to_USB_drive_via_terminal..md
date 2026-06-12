---
title: "[SOLVED] Moving files to USB drive via terminal."
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by 3ark on 2007-08-24
Hey this should be an easy one, but I could use some quick help. I messed up my ubuntu and can only see the terminal. I'm just gonna do a clean feisty install, but I want to copy some files to my USB drive first. I THINK the command I should use is something like this:

mv -r Pictures myusbdrive

The problem is that I'm not sure where 'myusbdrive' actually is. Is there some sort of quick command I can use to find that? I'd appreciate some help.:popcorn:

---

### Post by Dr Small on 2007-08-24
Look in /media
It should be called /media/usb or something.

Dr Small

---

### Post by Inxsible on 2007-08-24
```
sudo fdisk -l
```will tell you what drives are connected and then you can see which one of that is the one you are trying to find

---

### Post by 3ark on 2007-08-24
Thanks. :)

---

### Post by schorsch on 2007-08-24
Try
```
mount
```

---


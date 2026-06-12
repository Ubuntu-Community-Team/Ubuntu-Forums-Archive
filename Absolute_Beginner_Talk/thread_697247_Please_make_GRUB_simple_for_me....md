---
title: "Please make GRUB simple for me..."
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by TheSeb on 2008-02-14
I want to use GRUB, have it dual boot with windows and look "nice" as opposed to nasty dos-like. 

oh... and I don't want to read a book to do it.

I googled it up, but all i get is pages upon pages upon pages.

Isn't there some simple 1,2,3,4 step procedure to do this?

can someone please help?

---

### Post by PeterJS on 2008-02-14
Ask and ye shall recieve :)
[http://www.getdeb.net/app/Startup+Manager](http://www.getdeb.net/app/Startup+Manager)

---

### Post by computx on 2008-02-14
You are asking for 2 different things here so first I will tackle how to make grub look nice. Nice is pretty subjective but a good splash image goes a long way. Google for grub splashimage and you can find several nice ones. 
It should be in a .xpm.gz file format.
Download it and copy it to /boot/grub/
```
sudo cp imagename /boot/grub/
```
now edit /boot/grub/menu.lst with your favorite editor
and near the top add a line like this
splashimage = (hd0,1)/boot/grub/usplash.xpm.gz

This assumes that your /boot directory is on the 2nd partition on the first ide drive. Yours can be in a different partition. you can find out what partition it is on by looking at the output of the mount command.

If at first you don't see the image at boot then you didn't point grub to the right partition, try again.

---

### Post by santiagoward2000 on 2008-02-14
> **TheSeb said:**
> I want to use GRUB, have it dual boot with windows and look "nice" as opposed to nasty dos-like. 

oh... and I don't want to read a book to do it.

I googled it up, but all i get is pages upon pages upon pages.

Isn't there some simple 1,2,3,4 step procedure to do this?

can someone please help?

Hi!
I just installed it here using this guide:
[http://ubuntuforums.org/showthread.php?t=208855]("http://ubuntuforums.org/showthread.php?t=208855")
Goode luck!

---

### Post by computx on 2008-02-14
Secondly, ubuntu should have automatically made an entry for your windows when it was installed but if for some reason it didn't, then you need to edit /boot/grub/menu.lst and at the bottom add a section like this.

```
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
 The root line must point to where your windows is installed.
Grub has a unique nomenclature for drives. (hd0,0) would point to the first partition of the first ide drive.

---


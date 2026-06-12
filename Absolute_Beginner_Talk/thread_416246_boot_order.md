---
title: "boot order"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by daberkayboya on 2007-04-20
when my computer starts up it automatically starts up with ubuntu, how can i change this so that it will start up with windows xp first.

thanks ahead.
:guitar: :guitar: :guitar:

---

### Post by jtraub on 2007-04-21
Load in ubuntu. Open terminal and type


```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst
```

Find where line 
```
default         0
```
 is located in editor window

Replace that line with 
```
default         n
```
where n is entry number for Windows in grub menu. (Remember, that numbering starts from 0).
Save and reboot.

---

### Post by tbg58 on 2007-04-21
Boot up into Ubuntu, then open a terminal.
cd to /boot/grub
In the directory, first do 
sudo cp menu.lst menu.lst.bak (safety measure)

There, edit the file menu.lst by doing:
sudo gedit menu.lst
There is an entry there that says default=x where x is the number of the operating system that boots first.
Down in the bottom part of the file you will see the list of operating systems to boot.  They'll look like this:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37b152b7-52fd-44db-bea5-54c0fb760b50 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Each set like this is separated by a space.  Count down to the block for Windows XP. The first OS is number zero -- set the number of your Windows install as the default.
This should get you going!
Good luck!
= Rob

---

### Post by daberkayboya on 2007-04-21
thanks
:guitar: :guitar: :guitar:

---

### Post by jpmswiss on 2008-05-04
worked for me too! Thanks

---


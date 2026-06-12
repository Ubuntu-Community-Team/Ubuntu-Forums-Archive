---
title: "[SOLVED] Trouble with grub-install"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by King Mir on 2008-04-08
I'm trying to install Ubuntu, but it fails citing grub-install failed, fatal error, or something in that spirit. 

I got it working earlier, but then I was messing around trying to make grub boot windows XP, and now it won't work. Reinstalling Ubuntu doesn't work, as per aforementioned error.

I've tried a few things, but none of them worked.

---

### Post by zwygart on 2008-04-08
Hi,

Have you tried by removing completely the partitions swap and ext3 of Ubuntu.
When I tried to install Ubuntu over it self by selecting the partition ext3, it makes a error. I don't remember which. I then erased ext3 and swap and the extensioned partition. This way you install on free disk space. It worked for me.

Backup the menu.lst file

```
cd /boot/grub
cp menu.lst menu.lst_backup
```

After that edit the file menu.lst wich is in boot/grub or something
```
sudo gedit /boot/grub/menu.lst
```

To boot windows you have to add this at the end of the file:

```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

change hd0 by the number of your hard disk, counts begin with 0. The second 0 is the partition of your windows partition. You may try values. 

To see the grub at boot remove # of #hiddenmenu

Read the file for help.

N.B.: I'm on Windows now so I'm not sure about the place of menu.lst and the commands but it should help.

---

### Post by King Mir on 2008-04-08
> **zwygart said:**
> Hi,

Have you tried by removing completely the partitions swap and ext3 of Ubuntu.
When I tried to install Ubuntu over it self by selecting the partition ext3, it makes a error. I don't remember which. I then erased ext3 and swap and the extensioned partition. This way you install on free disk space. It worked for me.Thanks that worked!

> Backup the menu.lst file

```
cd /boot/grub
cp menu.lst menu.lst_backup
```

After that edit the file menu.lst wich is in boot/grub or something
```
sudo gedit /boot/grub/menu.lst
```

To boot windows you have to add this at the end of the file:

```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

change hd0 by the number of your hard disk, counts begin with 0. The second 0 is the partition of your windows partition. You may try values. 

To see the grub at boot remove # of #hiddenmenu

Read the file for help.

N.B.: I'm on Windows now so I'm not sure about the place of menu.lst and the commands but it should help.Tried all that. Didn't work. The problem is that I'm tri-booting with XP and Vista, and I wanted vista, ubuntu and XP to both boot from the same screen, instead having to select the vista bootloader in grub, and start either windows version from that. 

I tried to hide the XP installation from vista's installer. That worked: I wasn't able to log into XP after that. But then I was unable to get XP to boot from grub.

---


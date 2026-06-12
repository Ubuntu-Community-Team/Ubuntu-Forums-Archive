---
title: "Multiple OS bootup"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by valros on 2007-12-26
With Multiple OS's (Windows and Kubuntu on seperate partitions) how do you choose which to boot up as the default and how do you choose to bootup different partitions, my DOS boot menu's dont distinguish seperate partitions as bootable, only the whole drive.

---

### Post by dickohead on 2007-12-26
You should do a search for tutorials on using Grub.

---

### Post by valros on 2007-12-26
Would a simple answer suffice?

---

### Post by dizee on 2007-12-26
Kubuntu installs its own bootloader (GRUB) automatically which, so long as Windows is installed first, allows you to choose at bootup which OS you want to use. It looks something like [**this**](http://appuntiubuntu.files.wordpress.com/2007/06/grub_prima.png?w=381&h=211).

You can edit the GRUB configuration to select which OS to boot by default, among other things.

---

### Post by Tyke91 on 2007-12-26
It's called GRUB, not DOS. here's how you would change the default setup.

open a terminal and type
```
gksudo gedit  /boot/grub/menu.lst
```

then scroll down to the bottom, where you will see something that looks like a more detailed version of your boot selection table. It will choose the top one by default, so just cut and paste whichever one you want to the top.

---


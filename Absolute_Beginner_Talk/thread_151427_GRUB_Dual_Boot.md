---
title: "GRUB Dual Boot"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by belikralj on 2006-03-27
Hi. I have just tried to setup a dual boot system with Ubuntu and Red Hat Fedora. I was wondering, how should you change the GRUB file menu.lst, what is the synthax, because I have installed Red Hat boot loader to load Ubuntu and Fedora and I think i chose the wrong Ubuntu partition to load with grub.

My Ubuntu is on an 8G hda and Fedora is on a 20G hdb

Fedoras bootloader is default

here's the site I intend to follow with slight mods to the method
[http://os.newsforge.com/os/04/12/21/1852209.shtml](http://os.newsforge.com/os/04/12/21/1852209.shtml)

please help! :-k

---

### Post by belikralj on 2006-03-27
I solved the problem by cutting and pasting the menu.lst from ubuntu boot loader to /boot in fedora. Huray!!!!

---

### Post by zxee on 2006-03-27
I took a look at the link but it is trying to get you to not install the bootloader and having multibooted as many as 12 distros that's not my method. You can have ubuntu install grub to the partition rather than the mbr, and that's what I like to do. If you know what partition your install is on or if it is on the entire drive you can just install to hda. If you want the fedora install to be your primary grub you can set that up in your bios-just have hdb load first in bios.
You can then load ubuntu with this code in fedora's /boot/grub/menu.lst:
title Ubuntu 5.10
rootnoverify (hda)
chainloader +1

---

### Post by belikralj on 2006-03-27
what is the chainloader+1 part for?
and the rootnoverify??

I would like to understand the code better, and learn what exactly I was doing to make it work.

---

### Post by belikralj on 2006-03-27
Also, This was just a practice for learning to make a dual boot with my parents Windows XP which i really really don't want to mess up.

---


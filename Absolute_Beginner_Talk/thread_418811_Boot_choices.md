---
title: "Boot choices"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-04-22
Hi, This is my current configuration, one 80gb ide drive having dual boot between windows xp and Ububtu edgy, one sata drive dedicated to feisty (installed after removing ide). Now I can select in my bios and go to either of my drive and the results are ok. However I tried to keep** ide **as my first boot and added this to the menu.lst.

Title Ubuntu Feisty
root            (hd1,0)
savedefault
chainloader     +1

Also added this line to device.map
(hd1)   /dev/sda

I get error 17 "Cannot mount selected partition  " error, am I doing something wrong

---

### Post by old_geekster on 2007-04-22
Here is a thread that should help you:

[http://ubuntuforums.org/showthread.php?p=1545861](http://ubuntuforums.org/showthread.php?p=1545861)

Hope this helps.

---

### Post by mahiyar on 2007-04-22
Thanks old_g but thats not what I'am looking for, I'am looking for a way for choices to boot spanning hard disks.

---

### Post by mahiyar on 2007-04-23
***Bump**** please help

---

### Post by anaconda on 2007-04-23
it seems like you have installed the (feisty) grub to mbr of your sata disk and then you try to boot from the first partition of that disk (not from mbr!).

And the first partition isn't bootable. (mbr is)

so what you should do is to install grub also  to the beginning of your feisty partition.

Dont remember exactly, but I think it goes like this.
1. boot to your feisty
2 sudo grub-install /dev/sda1
the whole point is to install it to sda1 and not just sda , which is the mbr.. (assuming your feisty is in the first partition (sda1))


Another choice is to add feisty to your current menu.lst file (edgy?) without using chainloading. eg. copy the menu entry from feistys menu.lst to edgys menu.lst and adjust it so that it is pointing to the kernel on the right hd.

---

### Post by mahiyar on 2007-04-23
Thanks anaconda, I gave up on making ide my first boot drive and instead made sata my first drive modified the sata's menu.lst to accomodate the entries in ide. Works like a charm.

---

### Post by bulldog on 2007-04-24
Problems solved?

---

### Post by mahiyar on 2007-04-25
Thanks Bulldog, yes the problem is solved the way I described i.e making SATA my first boot disk and changing the menu.lst of the SATA drive. So now I no longer have to change boot priority from the BIOS, however I 'am still wondering why I could not do the same for the ide drive.

---

### Post by louieb on 2007-04-25
You probably could. using the configfile option. Heres one i have for example.
Check Herman's Dual Boot site in my signature for more information.
```
title PClinuxOS configfile
savedefault
configfile   (hd1,0)/boot/grub/menu.lst 
```

---

### Post by mahiyar on 2007-04-25
No louieb, the config file option does not work. As a matter of fact I tried loading the ubuntu in SATA by using CLI options in grub even using kernel lines but I get the same error.

---


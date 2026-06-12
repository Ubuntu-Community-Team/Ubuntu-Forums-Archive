---
title: "Grub Error 17 after upgrade"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by leep on 2007-02-10
Today, after the latest automatic upgarde, I rebooted my pc and obtained a

GRUB ERROR 17
cannot mount selected partition

Now, I cannot boot my pc nor I know ho to fix the error. Any idea?
I don't want to install everything again, losing all my data...
Thank you in advance,
S.

---

### Post by dannyboy79 on 2007-02-10
you need to pop in a live cd and then create a directory then mount your boot partition or main partition if you didn;t create a boot partition, then you need to edit your /boot/grub/menu.lst so that it is calling for the correct partition. i can't be more specific, if you need help this has been written about a  million times within this forum as well as gogle.

---

### Post by geek_Man on 2007-02-11
Danny, Danny, Danny...

Leep, can you post your menu.lst file? Boot from the live CD and type into the terminal "sudo gedit /media/name_of_drive/boot/grub/menu.lst". Post all the contents of that file. And also, the name_of_drive is just whatever drive your Linux partition is on. For me it was usbdisk (mind you, it's not hda or sda).

---

### Post by dannyboy79 on 2007-02-12
geek man, geek man, geek man.

Leep, just so you don't get all screwed up. if you're working on an ubuntu live cd and you DIDN'T take out your harddrives from your computer and re-hook them up via a usb adapter, then they WILL be hda and or sda depending on whether or not you have ide drives or sata drives. the best solution I can give you without having to spend hours trying to tell you what to do is for you to get the super grub disk. it'll reinstall grub where ever you want it to. it's an awesome utility to have. now most people will say, you don't need to download any extra software and that you can use a live cd. well that involves chroot'ing into your install running frmo a live cd etc etc. I feel that for newbies this is the easiest straight forward way to solve this. here is the link. [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

or, if you really want to tackle this yourself using a live cd, here is a great link to what you need to do. i found it right here in the forums already. [http://www.ubuntuforums.org/showthread.php?t=355833&highlight=grub+error+17](http://www.ubuntuforums.org/showthread.php?t=355833&highlight=grub+error+17)

good luck

---


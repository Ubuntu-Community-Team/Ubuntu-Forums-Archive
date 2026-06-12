---
title: "Grub. . ."
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by bobd104 on 2007-12-20
Hi Anyone, just loaded Ubuntu 7.10 Gutsy Gibbon yesterday and I'm very pleased with it.  It is very quick and from a user standpoint, it doesn't take much to get going with it.

Here's something I was wondering; can the GRUB Boot loader line sequence be modifed so that the item of your choice is first in line to boot?  Thanks for any input. . .

Bob D.

---

### Post by liberum on 2007-12-20
Sure, you just need to modify the grub menu.lst file

sudo gedit /boot/grub/menu.lst

After all the commented stuff there will be the linux entries.  You could rearrange them as you saw fit.  Although I personally think that just changing the "default" setting from 0 to the item you want would be easier.

BUT: when you update your kernel say you have 2.6.20-15 and you upgrade to 2.6.20-16
then this new item will be at the top of your list so it will boot automatically if your default setting is 0

Also note that grub starts its numbering with 0, so if you have the following partitions (after typing "fdisk -l")

sda1 - NTFS
sda2 - linux
sda3 - extended
sda5 - swap

then to grub they are hd0,0  though hd0,3
i.e. hdX,Y where X is the drive number (starting with 0) and Y is the partition number (starting with 0)

Here is more specific info
[http://ubuntuforums.org/showthread.php?p=1319395](http://ubuntuforums.org/showthread.php?p=1319395)

Hope this answers more questions then it creates

---

### Post by shadow-of-sin on 2007-12-20
Yeah you can change GRUB to the way you want it (including the order of boot options in the menu) by editing the /boot/grub/menu.lst file.

First make a backup just in case:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Then edit using gedit:
```
gksudo gedit /boot/grub/menu.lst
```

You can then arrange it the way you want.

EDIT: liberum beat me to it :D

---

### Post by bobd104 on 2007-12-20
Thanks to both of you for the quick response.  This is my second attempt at using Ubuntu.  It just keeps drawing me in?  Something about it that's just intriguing, captivating?  However, my kids like booting up to Windows and have no desire to delve into Ubuntu so I want the system to go to Windows by default without having to make selections. . .

---

### Post by malangaman on 2007-12-20
This is the best How to I have found to do what you ask.
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by liberum on 2007-12-20
Yes, Shadow is dead-on... make a back up first!

---


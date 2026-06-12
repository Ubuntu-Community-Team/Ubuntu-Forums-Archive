---
title: "Deleting Windows partition"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by arden on 2006-06-22
I have WK2 and Dapper on the same hard drive and want to delete the Windows partition. What is the best way as not to lose my Dapper install?

---

### Post by truNWA on 2006-06-22
get Gparted
```
sudo apt-get install Gparted
```

then when you open Gparted, it will show your 2 partitions, just check one for deltetion and confirm it.

---

### Post by arden on 2006-06-22
I have tried qparted and can see the partition I am trying to delete. The options are grayed out and will not let me delete. Am I doing something wrong?

---

### Post by fer5437 on 2006-06-22
Try gparted live cd.

---

### Post by aysiu on 2006-06-22
Try ```
sudo aptitude update
sudo aptitude install gparted ntfsprogs
gksudo gparted
``` and make sure the partition is unmounted.

---

### Post by shanepardue on 2006-06-22
after that partition is deleted. how do you just boot straight to ubuntu without having to go through grub?

AND, without grub, how do you enter recovery mode?

sorry for the overload of questions

---

### Post by aysiu on 2006-06-22
You'll always go through Grub--there's no other way to get to Ubuntu.

You can, however, change the timeout, so that it makes the default selection sooner (two seconds instead of five seconds).

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
``` Find the line that says ```
timeout 5
``` and change the 5 to 2 or 1. Of course, you could always make the timeout 0, but, as you pointed out, that would not allow you to enter recovery mode.

---

### Post by arden on 2006-06-22
[QUOTE=fer5437]Try gparted live cd.[/QUOTE]
Well I used qparted live cd and deleted Windows. Now I caint boot Dapper. I get  Grub Loading Stage 1.5 and Error 15 and nothing else. Any way to boot?

---

### Post by underdog on 2006-06-22
You should boot from a live CD and reinstall Grub, probably.

---

### Post by arden on 2006-06-22
How do I reinstall Grub from live CD? And I am running Dapper and dont have the live CD with me, can I use a 5.04 live CD?

---

### Post by underdog on 2006-06-22
This thread has some basic info, as well as a link to a guide.

[http://www.ubuntuforums.org/showthread.php?t=200374&highlight=reinstall+grub]("http://www.ubuntuforums.org/showthread.php?t=200374&highlight=reinstall+grub")

---

### Post by aysiu on 2006-06-22
[QUOTE=arden]How do I reinstall Grub from live CD? And I am running Dapper and dont have the live CD with me, can I use a 5.04 live CD?[/QUOTE]
You can use a Hoary live CD. Follow [these instructions](http://ubuntuforums.org/showthread.php?t=24113).

---


---
title: "instaled ubuntu and now computer wont boot anything"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by hessiess on 2007-05-04
i instaled ubuntu exactly foloing the instructions and now it wont boot windows or ubuntu, it gets to the grub bootloder, reastarts gets to the grub bootloder, restarts agean, and just ceeps dooing this. funny thing is it workd fine once last nite!. can i shut down the bootloder and just get intu windows or ubuntu? dont care witch, i need the computer for school in 2 howers!

---

### Post by Billy McCann on 2007-05-04
Download the Super Grub Disc.
[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

Burn it and boot into it.  go to GNu/Linux > Advanced > REstore GRUB > Automatically.

---

### Post by Slackpacker on 2007-05-04
You should be able to boot on a Windows CD or the LiveCD, or enter the boot menu when the machine restarts and boot your Windows partition, provided you didn't mess it up.  You probably need to provide more info about your hardware and what instructions you used in order for folks to help.

---

### Post by hessiess on 2007-05-04
> You should be able to boot on a Windows CD or the LiveCD, or enter the boot menu when the machine restarts and boot your Windows partition, provided you didn't mess it up. You probably need to provide more info about your hardware and what instructions you used in order for folks to help.

hp pavilion dv2000.
carnt find a boot menu, can only acsess the bios.
i havent got a boot cd, the schools got it! its on a separate partition of the disk

---

### Post by hessiess on 2007-05-04
has this hpened to anyone else before?

cernt burn a iso, it was the only computer in the house that could do this. havfent got time to downlad anything anse

---

### Post by antoz on 2007-05-04
If you are in a jam try using the live CD and select boot from Harddisk it may work till you have time to fix it.

---

### Post by hessiess on 2007-05-04
> **antoz said:**
> If you are in a jam try using the live CD and select boot from Harddisk it may work till you have time to fix it.

it dos the same as just turning it on, gets stuck in a infanate loop of restarting itself:(

---

### Post by seshomaru samma on 2007-05-04
boot from the liveCD
reinstall Grub like this:

open a terminal (look in applications >accessories )and enter these commands:
```
grub
```
```
find /boot/grub/stage1
``` 
this will print something like (hd0,1),replace the question marks in the next command by whatever the output was:

```
root (hd??)
```
(probably (hd0,1)
then
```
setup (hd0)
```
```
quit
```
if you get any errors ,post them here

---

### Post by hessiess on 2007-05-04
i think ive found part of the problem, but dont know what to do about it. atlest i can get it to boot xp now. 

grub wotks fine untill i boot xp. if i shut down xp and reboot then it alwase fails. xp is doing somthing to it but i dont know what. 

any ideas?

thx

---

### Post by hessiess on 2007-05-04
no idea what my problem is?:confused:

---

### Post by hessiess on 2007-05-05
bump

---


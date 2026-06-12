---
title: "How do you change your active partition?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by masterspy7 on 2006-07-20
Sorry if I posted this in the wrong forum, but using the ubuntu live cd is there any way I can change the active partition to the windows partition so I can boot into windows? Is there any command I need to use? Any help would be appreciated!

---

### Post by Paerez on 2006-07-20
If it is currently booting linux, you have two choices:
1) Teach linux how to boot windows, this is a "dual boot"
2) Erase linux's booting power (but not linux) and let windows control who boots. Then windows can be set to boot linux (I don't know how to do this, but it can be done).

To do 1, please post me the following file:
```
gedit /boot/grub/menu.lst
```

---

### Post by ovimunt on 2006-07-20
What do you mean exactly? Have you installed Ubuntu and are now trying to boot in Windows?

---

### Post by masterspy7 on 2006-07-20
I have a broken partition that is currently active so I want it to completely boot into windows, not dual boot.

---

### Post by shanepardue on 2006-07-20
if you're saying you don't have ubuntu anymore and you want to only boot into windows and windows alone, then restart the computer with the windows cd and get to the recovery console.

at the command prompt, type the following

```
fixmbr
```

you're good!

---

### Post by masterspy7 on 2006-07-20
Thanks! But I have one question. Will that erase any of my Windows data or will it just change the active partition (sorry if this is a stupid question).

---

### Post by Paerez on 2006-07-20
It will just boot to your windows. no erasing.

Exactly as shane said. Put in your XP CD, boot it (you have to press a key to make it boot). Press R at the menu to choose a recovery console. Then wait a while, then press 1 to choose the Windows directory, when it asks you for an admin password, put it in (if you are unsure, just hit enter) then type "fixmbr"

good luck.

---

### Post by shanepardue on 2006-07-20
it'll only affect your boot record..all of your windows data will be fine.

---

### Post by masterspy7 on 2006-07-20
Thanks!

---

### Post by masterspy7 on 2006-07-20
Oh shoot!!!! When I boot after doing fixmbr it just says error loading operating system!!
What should I do!
I know I have 

C:/ where windows is installed
and
D:/ Empty Drive

---

### Post by shanepardue on 2006-07-20
fixmbr restores the bootloader to it's original state. it may be the windows installation at this point. i'm not completely sure though.

---

### Post by masterspy7 on 2006-07-20
Am I screwed? I have really important info there, I should've backed it up! Do you think spfdisk can do anything? I've heard it can also change the active partition. And If I reinstall windows does that mean I lose all of my windows data?

Edit: Used Spfdisk, changed partition, works fine now, thanks for your help anyway!

---


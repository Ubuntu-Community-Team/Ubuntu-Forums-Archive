---
title: "Dual Boot - Default booting option"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by candyoff on 2006-10-05
Hi

Currently my pc is dual booting with Windows XP and Ubuntu. 
So, everytime I start my comp, It will go to the booting menu. The current booting default is Ubuntu, can I know how can I change it to Windows Xp?

Regards

---

### Post by risbac on 2006-10-05
In a terminal: 

> sudo gedit /boot/grub/menu.list

Then look at the comments at the beginning, they explain how to select one entry instead of another one. You can just move XP at the top also, it should work.

---

### Post by devils_casper on 2006-10-05
in /boot/grub/menu.lst the line 'default' points to the default OS.
if you have only WIndows and Ubuntu then change its value to 4.

sudo gedit /boot/grub/menu.lst

look for default 0 line. its 4th or 5th line. change **default 0**  to **default 4**.





casper

---

### Post by candyoff on 2006-10-05
hi Casper & risbac

Thanks for the fast reply!
It worked!
Your time is appreciate!
:)

Regards

---

### Post by Pjotr123 on 2006-10-05
Having Windows XP as default boot option is not such a good idea, I think. Windows XP is a fairly adequate operating system, but much too unsafe for the internet. Please keep your PC and the internet healthy, and use only Linux for internet!

Greeting, Pjotr.

---

### Post by louieb on 2006-10-05
If you make XP the default buy moving it to the top of the list. Make sure you place it **[SIZE="3"]above[/SIZE]** the line that reads:
```
### BEGIN AUTOMAGIC KERNELS LIST
```
If you don't then the next time there is an update to the kernel your XP entry will disappear.
The other safe place for the entry is **[SIZE="3"]below[/SIZE]** the line that reads:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

In this case you would have to edit the default option number after a kernel update.

---


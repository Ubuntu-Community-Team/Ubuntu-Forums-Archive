---
title: "GRUB question"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by trizuk on 2007-04-13
is it possible to have GRUB's menu look like this:

1. boot ubuntu
2. boot windows 2003
3. boot windows xp


instead of sending me to the windows chainloader(?)

id like to have all my OS options under one menu

is this possible? thank you in advance.

---

### Post by Doug11 on 2007-04-13
Try do a search for    ...restore grub...it should come up with something,,,if I come across the right link,,I'll post it,,but yes,,it is possible

---

### Post by Doug11 on 2007-04-13
Here you go,,,try this

[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

---

### Post by trizuk on 2007-04-13
i used that guide before when vista messed up my bootloader, but i dont think that guide talks about editting the menu.1st in /boot/grub. sorry for not mentioning that before. thanks

---

### Post by seamus7 on 2007-04-16
(oops sorry i think you are asking a different question)

My Grub looks like this..

Three Machine Minds
1. Ubuntu Edgy Eft
2. Linux Recovery Console
3. Windows Vista Home



* I just edited the title fields for each operating system listed in menu.lst  ... I always install windows first then ubuntu ... it automatically installs grub in the Master Boot Record and automatically discovers windows.. it worked this way when I had dapper and windowsxp too

---

### Post by breezyfox on 2007-04-16
> **trizuk said:**
> is it possible to have GRUB's menu look like this:

1. boot ubuntu
2. boot windows 2003
3. boot windows xp


instead of sending me to the windows chainloader(?)

id like to have all my OS options under one menu

is this possible? thank you in advance.

Hi , II think it is possible, have a look at the following link.
[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

hope this helps

bz

---


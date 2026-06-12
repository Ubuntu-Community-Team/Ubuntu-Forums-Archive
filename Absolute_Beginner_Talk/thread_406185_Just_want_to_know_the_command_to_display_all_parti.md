---
title: "Just want to know the command to display all partitions and their sizes"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-10
Hey, just want to know the specific command that displays every partition in the comp. and their sizes.

Additionally, does anyone know what GRUB is? and why is it the most used.

---

### Post by Dekunuts on 2007-04-10
you don't really need a command, just check the system monitor app, you can find it in the system menu. It shows you what processes are running and shows information on your mounted drives. I hope that helps you. 


GRUB is a bootloader, it has a list of the different operating systems on your pc and allows you to pick which one you want to boot. Every time you install a new kernel for your ubuntu installation, it shows up as a new entry, just so you know.

---

### Post by Maestro23 on 2007-04-10
Grub: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Display partitions:

> df -h

---

### Post by robenroute on 2007-04-10
> **Parasitesss said:**
> Hey, just want to know the specific command that displays every partition in the comp. and their sizes.

Additionally, does anyone know what GRUB is? and why is it the most used.

But if you do want a command, check (man) the df command.

---

### Post by Parasitesss on 2007-04-10
Thank you very much, but one more question, you said that "Every time you install a new kernel for your ubuntu installation....." why would you want to install a new kernel in the first place?

---

### Post by robenroute on 2007-04-11
> **Parasitesss said:**
> Thank you very much, but one more question, you said that "Every time you install a new kernel for your ubuntu installation....." why would you want to install a new kernel in the first place?

No piece of software is perfect.... same goes for the Linux kernel. When memory leaks and/or other security issues are discovered, bugs resolved, functionality enhanced, etc., a new kernel is released (more or less). Sometimes it's good to update/upgrade your kernel in order to have a safer system or to resolve a driver issue.

---

### Post by Parasitesss on 2007-04-16
cool. very cool thankyou

---


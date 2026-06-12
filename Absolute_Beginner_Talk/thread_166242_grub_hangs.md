---
title: "grub hangs"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by alexuser on 2006-04-26
Hello!

Can anybody help with the next problem:

I tried to install 5.10 and got some troubles with grub(?). I have two HDD: IDE and SATA. The IDE HDD is main. There is my boot manager on the one (os/2 boot manager). 
I have install Ubuntu on /dev/sda2 and install grub to the boot record of the same partition. Then I add this partition to my boot manager. When I try to run Ubuntu the string "GRUB loading stage 2" (or something like) appears only and system hangs. 

How it can be fixed?

PS The system is on the K8T800Pro chipset with 8237

---

### Post by htinn on 2006-04-26
How exactly are you booting into grub? Are you using the BIOS to get to grub, or are you booting into some other boot manager and then using that to load grub?

---

### Post by alexuser on 2006-04-26
I load grub via other boot manager.

---

### Post by htinn on 2006-04-26
If it's possible, you really should configure BIOS to boot grub directly. I don't think grub will work, otherwise.

---


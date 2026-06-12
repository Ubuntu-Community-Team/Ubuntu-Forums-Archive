---
title: "[SOLVED] Boot XP first"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Coolride on 2007-10-23
How can a change the boot sequence  to load XP first, I usually walk by the PC in the morning and hit the power, and need XP there without any assistance for now. Thanks, I'm 
just starting out with this Linux system.

---

### Post by overdrank on 2007-10-23
> **Coolride said:**
> How can a change the boot sequence  to load XP first, I usually walk by the PC in the morning and hit the power, and need XP there without any assistance for now. Thanks, I'm 
just starting out with this Linux system.

Hi and welcome, you will have to edit the grub so that XP will boot first. This link has great info 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Good luck! :KS

---

### Post by be4truth on 2007-10-23
do a backup first

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

type this into a terminal

```
sudo gedit /boot/grub/menu.lst
```

right at the top is one line 
default		0

change the 0 to the number where your Windows XP is listed. Depending on how many kernels are lsited it could be a 5 or 8. Then save and reboot. You can check where the automatic choice is. If it is wrong adjust the number.

---

### Post by Coolride on 2007-10-23
Thanks everyone, it worked great, and while I was in the menu I changed the timeout too.

---

### Post by be4truth on 2007-10-23
Pls mark the thread solved. Go to Thread Tools at the top of this page to do so. Have fun.

---


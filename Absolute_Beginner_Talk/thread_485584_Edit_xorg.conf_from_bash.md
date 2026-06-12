---
title: "Edit xorg.conf from bash"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Loki1989 on 2007-06-27
X wont start after I installed Ubuntu on one pc and shifted the drive cause the other wouldn't boot the cd. I and going to try it agains here in a minute and will post my findings. I have a AMD Sempron 3000+, the motherboard is a MSI K9VGM-V, with 512 Mb PC2 4200 RAM, A 40 Gb Hard Drive and a CD Drive




okay just restart the computer and in recovery mode start the sudo dpkg-reconfigure xserver-xorg

---

### Post by eentonig on 2007-06-27
just type the following command in the cli

> sudo dpkg-reconfigure xserver-xorg

This will reconfigure your X server to recognize your hw.
You will have to provide some answers with this run.

---

### Post by Loki1989 on 2007-06-27
I have tried and it causes a kernel panic every time and my computer doesn't boot from a CD-R so I will try to configure a DVD-ROM into it after tomorrow when I get off work.

---

### Post by kerry_s on 2007-06-27
[B]sudo nano /etc/fstab
[/B]
you have to point to the new location

you should do yourself a favor and install mc.

**sudo apt-get install mc**

**sudo mc ** <for root
**mc** <for non-root 

not really needed but if you want the mouse with mc

**sudo apt-get install gpm**

---

### Post by Loki1989 on 2007-06-27
Now Ubuntu Doesn't boot at all it loads I try to log in and it has a kernel panic I am still trying though.

---

### Post by Loki1989 on 2007-06-27
okay just restart the computer and in recovery mode start the sudo dpkg-reconfigure xserver-xorg

---


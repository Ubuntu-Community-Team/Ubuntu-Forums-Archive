---
title: "non-system disk after install"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by maddog1711 on 2006-09-07
I am getting frustrated now. I have tried to install Ubuntu and Kubuntu onto a clean disk drive by using the Live CD and the install link. Everything appears to go well but when the system re-boots I get the Non-system disk error after the BIOS has run its POST checks. I have used QTparted to format th edrive with a linux swap partition and have changed th edrive to Fat32. It has also ben formated as Ext3. What am I doing wrong?

---

### Post by bigken on 2006-09-07
you need to set a bootable flag you can do this using qtparted ie make the disc bootable ;)

---

### Post by maddog1711 on 2006-09-07
Is that one of the menu option if so which one?

---

### Post by bigken on 2006-09-07
down load this and make your disc bootable [http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/)
or download this 
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
i would also check the bios make sure your hdd is showing ;)

---

### Post by maddog1711 on 2006-09-14
Problem solved. It helps if you make sure the BIOS can see the drives. I had switched off the interface and forgotten to put it back on. A basic error from a non-novice. Doh!

---


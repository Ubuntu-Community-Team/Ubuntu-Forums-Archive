---
title: "booting default windows"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by kattou22 on 2008-04-16
Hi i was wondering if its possible to boot  off a boot disk so that my son when he uses the pc it would boot automatically in windows XP . I tried not installing Grub and tried installing LILO instead but i could not install that during installation. So i have grub installed.  If its not possible to boot off boot disk then how to change to boot default windows xp .   I tried E to edit command line in boot screen...   it does not work

---

### Post by mbadawi23 on 2008-04-16
So, I think what I understand that you want your computer to boot automatically into WinXP, right?

if this is the case, then you can setup Grup to default to Windows with a time pause, let's say, 10 seconds. This link may be helpful:
[http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html]("http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html")

---

### Post by smurphy_it on 2008-04-16
Jump in a terminal and type sudo gedit /boot/grub.menu.lst

By default, grub will default to 0.  That is your first entry.  If you want it to use another one, just tell it the #entry to use, or make XP your first choice.

Example list

Windows xp
chainloader etc...etc...

Ubuntu 2.6.22-14.generic
etc...etc...

Above Windows Xp is choice 0, Ubuntu is #1, etc....

Hopefully that is clear.

---

### Post by northern lights on 2008-04-16
You can edit the GRUB menu you see upon booting via ```
gksu gedit /boot/grub/menu.lst
```
Locate the "Windows" entry, cut and paste it to the top, i.e. above all the "Ubuntu" entries. Save and exit. Done.

---

### Post by Norman Grahams on 2008-04-16
Take note that if you refer to it by its number, the spacer in between the ubuntu entries and the windows entries also takes up one number.
And as smurphy_it pointed out, the first entry is 0 not 1.

---


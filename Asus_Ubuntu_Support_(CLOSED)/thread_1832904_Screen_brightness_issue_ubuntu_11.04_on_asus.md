---
title: "Screen brightness issue ubuntu 11.04 on asus"
date: 2011-08-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Kirstine on 2011-08-25
Hey!

I just got Ubuntu 11.04 on my Asus UL80V and have the same problem as in 10.04, where the screen brightness doesn't change if using the Fn with F5 and F6. I could fix it in 10.04 but now I can't.

I've tried this:


"sudo gedit /etc/default/grub

Editing the lines:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub"


Nothing changes so i tried this: 


sudo gedit /etc/X11/xorg.conf


but then this comes up:


"(gedit:4256): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.CYAS0V': No such file or directory

(gedit:4256): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory"


I hope you can help me,
thanks for reading! :D

---

### Post by tzily on 2011-08-25
1. did you try to restart ? sometimes this happens
2. you forgot to check it the easy way,  from the power management options: set display britness to %

---

### Post by Kirstine on 2011-08-25
yea restarted and repeated several times

doesn't work either :)

---

### Post by tzily on 2011-08-25
what about number ''2.'' ?

find your power management and manually modify it

edit: see if gksudo gnome-power-preferences from terminal works ;)

---

### Post by Kirstine on 2011-08-25
it doesn't work in power management either

---


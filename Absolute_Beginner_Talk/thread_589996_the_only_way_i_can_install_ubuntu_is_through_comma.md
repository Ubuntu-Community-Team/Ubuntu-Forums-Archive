---
title: "the only way i can install ubuntu is through command line"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by easy rhino on 2007-10-24
i must install ubuntu using the command line install from the alternate disk. however after a successful base install i need to install the latest fglrx driver for my x1800xt. i cannot simply install ubuntu-desktop because the video drivers that come with ubuntu by default kill the signal to the monitor. does anyone have a howto on installing gutsy from the command line and installing fglrx and then ubuntu-desktop ?

---

### Post by Inxsible on 2007-10-24
silly question, but I shall ask it anyway. Have you tried the LiveCD. Does everything work when you are in LiveCD mode?

---

### Post by scrooge_74 on 2007-10-24
> **easy rhino said:**
> i must install ubuntu using the command line install from the alternate disk. however after a successful base install i need to install the latest fglrx driver for my x1800xt. i cannot simply install ubuntu-desktop because the video drivers that come with ubuntu by default kill the signal to the monitor. does anyone have a howto on installing gutsy from the command line and installing fglrx and then ubuntu-desktop ?

have you tried sudo apt-get install fglrx-driver from a command line?

---

### Post by P4man on 2007-10-24
you can always change the videodriver to VESA if the one chosen by ubuntu installer doesnt work.

If you end up with a black screen, just press ctrl+alt+F2.This brings you to text mode, so should be displayed even if X is screwed.  Log in. Then edit the xorg.conf by typing:

sudo nano -w /etc/X11/xorg.conf

change ATI (or Radeon) to vesa. More likely though, try changing the resolution/refresh rates. To start  the graphical interface again, type:

sudo nano /etc/init.d/gdm restart

---

### Post by easy rhino on 2007-10-24
> **Inxsible said:**
> silly question, but I shall ask it anyway. Have you tried the LiveCD. Does everything work when you are in LiveCD mode?

i have tried the live cd (first thing i tried) and it appears to boot ubuntu but then i see lines across the monitor and the monitor turns off. i have gottan 7.04 working through the command line and fglrx installed without a problem but it appears that with 7.10 installing xorg effect xorg.conf differently.

---

### Post by easy rhino on 2007-10-24
> **scrooge_74 said:**
> have you tried sudo apt-get install fglrx-driver from a command line?

yea, i believe it is sudo apt-get install xorg-driver-fglrx

that installs the driver but then what?? should i install xorg next?? then reboot and edit xorg.conf ?

it just appears to me that the process changed from 7.04 to 7.10

---

### Post by scrooge_74 on 2007-10-24
you can install X and then the driver, later you can do a sudo dpkg-reconfigure xserver-xorg  and pick the correct driver

---


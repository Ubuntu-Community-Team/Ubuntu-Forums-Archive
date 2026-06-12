---
title: "ubuntu-desktop"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by maji on 2006-08-10
With a LAMP installation of dapper drake server I type the following commands to install a gui:

sudo apt-cdrom add (with the ubuntu-6.06.1-desktop-i386 disc in the drive)
sudo aptitude update (no network configuration at this point)
sudo aptitude install ubuntu-desktop

The system replies:

"Couldn't find any package whose name or description matched "ubuntu-desktop""

Surely the desktop version of dapper drake has the package "ubuntu-desktop"? Or is the ubuntu-desktop package only found on the "alternate" disc?

---

### Post by bigken on 2006-08-10
at the the promt i think you need to type 

[B]sudo nano /etc/apt/sources.list 

[/B]and uncomment the cdrom or add the cdrom

---


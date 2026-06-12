---
title: "How to run installation ISO from external hdd?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-05-13
How can I run the ISO installation files off of my external hard-drive? My internal CD-ROM is broken, and my computer can't detect my external cd-rom. I have the Feisty ISO and would like to boot the installation CD off of my external hdd.

---

### Post by skwishybug on 2007-05-13
Do you happen to have windows installed on your machine?

If so, theoretically you can extract the .iso to that drive using winRar and then if you can set your computer to boot from that drive, it should work.

The caveat is that I have had success using a similar method for extracting and installing iso files for a couple of windows programs, but do not know if it will work for installing Feisty or not.

---

### Post by FuturePast on 2007-05-13
Interesting problem. Maybe this will give you some ideas [http://www.bobpeers.com/linux/hard_drive_install](http://www.bobpeers.com/linux/hard_drive_install)
Alternatively you could try a net install.

Which OS do you currently have? Do you have a floppy drive?

---

### Post by syalam on 2007-05-13
Currently I am running Windows XP SP2. I tried extracting the ISO to the HDD but no luck booting from it.

---

### Post by FuturePast on 2007-05-13
Maybe try the instructions at the bottom of thios page: [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

---

### Post by skwishybug on 2007-05-13
Too boot you would need to do two things.

1. make sure that the extracted ISO is at the root of the drive, not in a directory

2. Set the system BIOS to boot from your USB first, not the hard drive or CD-ROM
(Usually this is a setting under a "Boot" option in the BIOS. Depending on your system, you can enter your BIOS by pressing the Delete key or F10 during start up).

---


---
title: "[SOLVED] URGENT! gui is completly ruined!"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-10-18
after installing gutsy i used the appearance menu(i think thats what its called idk cant remember but its the menu that detects the screen monitor)  after i selected my screen brand(samsung, syncmaster 931b vga) and reso of 1280x1024, i rebooted now the gui is tootally stuffed up, four screens everythings a mess cant read anything!! how do i revert to the previous settings? ill have to do this in the recovery mode using the CLI and i dont know what to do!! because i cant do anything throught the gui anymore :S, someone please help!!

---

### Post by NilsE on 2007-10-18
Try this in a terminal (command line)

sudo dpkg-reconfigure -phigh xserver-xorg

This will only make you go through the video setting in xorg.

---


---
title: "Trying to configure a dialup connection"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by eddie57 on 2006-03-21
I recently installed Ubuntu 5.10 and the installation went fine, although everytime i try to configure a dialup connection it says "modem not detected" even though my modem is listed in the hardware devices window. Also i tried issuing the "pppconfig" command from the terminal window and it said must be logged in as root so i issued the su command. when i entered the password it said authentication failure, so i issued the su command follow by my user name and then it accepted my password. Why did it have to have my user name even though i was already logged on under that name??

---

### Post by eriefisher on 2006-03-21
First you should use "sudo" for root access.

To set up dial up goto System>>Admin>>Networking>>???? You should find where to set up the modem. If you click on the connection and then properties, you can auto detect and set everything up. As for the path, I'm going from memory here as I'm away from my Kubuntu box, but dig in the menu and you will find it.

eriefisher

---

### Post by wolfmaniac on 2006-03-22
is ur modem an internal one?

bec all those are winmodem and linux do not support the drivers for them they wont b detected.
visit linuxaunt.com or linmodem.org/com(juz check) for more details.

---

### Post by nala on 2006-03-22
Configuring dial-up for Ubuntu is incredibly difficult since drivers for modems are not open-source. I personally decided that it was easier to have my machine dual-boot with Windows. Of course, it doesn't help that Conexant actually charges for linux drivers for their modems. There are some modems out there that are more Linux friendly (hardware modems). Perhaps consider buying one.

---


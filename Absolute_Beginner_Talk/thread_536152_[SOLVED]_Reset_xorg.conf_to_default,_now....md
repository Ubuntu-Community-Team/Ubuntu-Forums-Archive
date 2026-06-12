---
title: "[SOLVED] Reset xorg.conf to default, now..."
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by YAOMTC on 2007-08-27
Due to my overly-hasty editing of the xorg.conf file (for the Marble Mouse USB fix), I had to reset xorg.conf to the default (using sudo dpkg-rec...) Now I have to choose a video card driver for the X server. I look through the list, and I don't recognize anything. My motherboard has the Intel GMA 945G... And I don't see anything like that. Should I be looking for something else?

[SIZE="1"](No worries, that was my first time editing the xorg.conf. Nothing important was ruined.)[/SIZE]

---

### Post by ThrobbingBrain66 on 2007-08-27
You'll want to choose either the i810 module or the Intel module.  Making a backup of a file is never a bad idea :)

---

### Post by DarkN00b on 2007-08-27
Choose the i810 driver if you have it installed. If you simply have no idea which drivers you have installed, choose "vesa". You'll have no 3d acceleration, but you will be able to boot into X to download the drivers you need.

---

### Post by YAOMTC on 2007-08-27
The i810 worked, thanks!

[SIZE="1"](Note: After I selected the driver, a strange gray screen with an X for a seemingly useless cursor appeared. I had to restart the computer, but there were no problems after that.)[/SIZE]

---


---
title: "Instlled Breezy in Laptop: No Video"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by totfit on 2006-01-28
Just installed Ubunto on my Compaq Presario 2100 and have no video. I installed a couple of weeks ago on my PC and have been a convert from windows since, but having problems with the laptop. This was my second try. The first time I set the resolution too high during installation of packages. I reinstalled with the proper resolution checked, but have no video. I get the Ubuntu graphic splash screen during boot, then the screen goes black. I hear the "drum" sound that happens when the sign on window appears, but there is a black screen. I am a neophyte with Linux, Gnome, Debian, Ubuntu, except for my two weeks experience with my PC. I would appreciate any help. I am currently on the recovery screen awaiting a command line, but have no clue what to input to start working on the problem. 

Thanks in advance

---

### Post by DonQuixote on 2006-01-28
Posting your graphics card maker and model would be a step in the right direction in getting help.  I'm fairly new also, but more details help.

John

---

### Post by kaamos on 2006-01-28
Try this: when you have heard the drum sound, press ctrl+alt+F1. You should be able to login from there. You can now use the command
```
sudo dpkg-reconfigure xserver-xorg
``` to change your video settings. One (backup) solution would be to change the driver to "vesa", as this probably works most often. You can then restart the login screen with
```
sudo /etc/init.d/gdm restart
```

---

### Post by totfit on 2006-01-28
Thanks for the help. Had to leave for a bit. I'll try this now.

---

### Post by totfit on 2006-01-28
Okay, I took all the steps and checked the configurations. From what I have seen everything is set up with the graphics correctly. For some reason the failure seems to be in getting into the gnome desktop or making it visible. I would appreciate any help with this.

Thanks

---

### Post by totfit on 2006-01-28
Oh well, just bugged out and reinstalled windows.

---


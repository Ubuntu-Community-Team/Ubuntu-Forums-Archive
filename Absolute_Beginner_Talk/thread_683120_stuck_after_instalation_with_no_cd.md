---
title: "stuck after instalation with no cd"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by sneakmonkey on 2008-01-30
I'm new to linux and all of this is far beyond me but I've looked around for resolutions before I came here. I've installed ubuntu using this method [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) because my cd burner doesn't work and I don't have a floppy drive. Doing it this way didn't bring up a graphical install to simplify things but I managed to get my drive partitioned and everything installed correctly I'm sure.

But now I log in and its still at the DOS/BIOS like screen and I have no clue what to do next. It just sits at the black screen with my username and blinking cursor expecting some command of some sort. This so far over my head I have no idea where to start with commands and such. I'm curious about linux and I would like to try it over windows but if I cant get this problem solved I'll just wait until I can get my hands on a cd and take the more practical route of installation.

---

### Post by Crumpets and Jam on 2008-01-30
> **sneakmonkey said:**
> I'm new to linux and all of this is far beyond me but I've looked around for resolutions before I came here. I've installed ubuntu using this method [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) because my cd burner doesn't work and I don't have a floppy drive. Doing it this way didn't bring up a graphical install to simplify things but I managed to get my drive partitioned and everything installed correctly I'm sure.

But now I log in and its still at the DOS/BIOS like screen and I have no clue what to do next. It just sits at the black screen with my username and blinking cursor expecting some command of some sort. This so far over my head I have no idea where to start with commands and such. I'm curious about linux and I would like to try it over windows but if I cant get this problem solved I'll just wait until I can get my hands on a cd and take the more practical route of installation.

It might be more simple to [install from a USB Memory Stick]("https://help.ubuntu.com/community/Installation/FromUSBStick") if your computer has a USB port. If you get really stuck you can order a **free** (postage is free too) CD of Ubuntu 7.10 from the [Official Ubuntu ShipIt Service]("https://shipit.ubuntu.com/").

Hope that helps. Good luck.

---

### Post by Samhain13 on 2008-01-30
Try Ctrl + Alt + F7.

If that doesn't get you to a graphical login screen, go back to Ctrl + Alt + F1 and try:

```
sudo /etc/init.d/gdm restart
```

If that still doesn't work, try reconfiguring your xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

That will take you to some kind of text-based wizard to help you with the configuration.

---

### Post by sneakmonkey on 2008-01-30
thanks guys, il give the commands a try, otherwise il try booting from a flash drive. and if worse comes to worse il order the cd

---

### Post by Shazaam on 2008-01-30
Another possibility---
Do you get any errors about X not starting?
If not it sounds like you may have installed a version with no gui (minimal or server). If you have internet connectivity with your Ubuntu install  try these codes at the prompt.
First type this in.....
```
sudo apt-get update
```
It will ask you for a password (this will be your USER password) type it in and hit enter
Then enter this....
```
sudo apt-get install ubuntu-desktop
```
Or this if you want kde....
```
sudo apt-get install kubuntu-desktop
```
If you get any errors write them down and post back.
If everything installs correctly enter....
```
sudo reboot
```
Hopefully you will be greeted with a splash screen with a place to login.

---

### Post by sneakmonkey on 2008-01-30
Shazaam: I didnt get any errors but 

code: sudo apt-get install ubuntu-desktop

was not recognized as a command and

code: sudo apt-get update

did do something, it seemed like it was getting files to update or check if there were updates but it didnt really seem to do much

il post pictures of what it looks like, although low quality it might help my problem to let you see whats going on

---

### Post by sneakmonkey on 2008-01-30
[http://i227.photobucket.com/albums/dd79/sterkadoo/loginscreen.jpg](http://i227.photobucket.com/albums/dd79/sterkadoo/loginscreen.jpg)

this is the login screen

[http://i227.photobucket.com/albums/dd79/sterkadoo/afterlogin.jpg](http://i227.photobucket.com/albums/dd79/sterkadoo/afterlogin.jpg)

and what i get after logging in

[http://i227.photobucket.com/albums/dd79/sterkadoo/afterupdatecommand.jpg](http://i227.photobucket.com/albums/dd79/sterkadoo/afterupdatecommand.jpg)

and what happened after running the update command

---

### Post by Shazaam on 2008-01-30
Try samhain13's SECOND command and when it asks if you want it to auto-detect your videocard choose "No" and this will let you select "vesa" as the driver. Choose the default answers until you get to the section about your monitor, choose the second option (Medium) and then choose the resolutions you want by moving the highlight down to a choice (such as 1280x1024) and then tap your spacebar to check it or uncheck.

---

### Post by sneakmonkey on 2008-01-30
tells me i dont have xorg installed, is it something i need?

---

### Post by Samhain13 on 2008-01-30
Hummm... is your machine already connected to the Internet? I'm a bit intrigued as to why "sudo apt-get install ubuntu-desktop" doesn't work. Perhaps it returned an error because Ubuntu wasn't able to find the package/s as it wasn't connected to the repositories?

Anyway, I found this discussion:
[http://www.linuxforums.org/forum/debian-linux-help/41622-new-linux-ubuntu-install-gui-problem.html](http://www.linuxforums.org/forum/debian-linux-help/41622-new-linux-ubuntu-install-gui-problem.html)

You might find something useful there as the posters spoke of installing xorg.

---

### Post by sneakmonkey on 2008-01-30
> **Samhain13 said:**
> Hummm... is your machine already connected to the Internet? I'm a bit intrigued as to why "sudo apt-get install ubuntu-desktop" doesn't work. Perhaps it returned an error because Ubuntu wasn't able to find the package/s as it wasn't connected to the repositories?

yeah im connected to the internet and ive currently got windows xp professional installed

---

### Post by Samhain13 on 2008-01-30
Please see my previous post again, I edited it. There's a discussion that I found elsewhere that may offer a solution.

---

### Post by sneakmonkey on 2008-01-30
thank you for helping me this far i really appreciate it :)

il come back and update if any of the suggestions in the forum you linked end up fixing my problem

---


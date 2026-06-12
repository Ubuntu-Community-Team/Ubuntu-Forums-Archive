---
title: "ATI Driver"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by mjmjohn on 2006-03-27
Well-- I'm an absolute newbie to Linux and Ubuntu. Have a i386 Intel PC with XP and Virtual PC INstalled. I can set up Ubuntu on the virtual HD and it installs and  loads fine......Have a PCIe-16 ATI X1300X video card, and it really scrambles the output to the monitor. The forum has a lot of suggestions on how to fix this, but I need some really basic help. Like how to load different video drivers at startup. Thanks for your help in advance.

---

### Post by Sutekh on 2006-03-27
Okay you need to change the driver that X is currently using.

First backup and edit the X configuration file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```
 - When prompted for a password use your user's password

 - Those commands are case sensitive so make sure its X11 not x11 (or just copy and paste the commands)


When the file opens move down until you reach the section entitled
```
Section "Device"
```
Change the line that contains
```
Driver "ati"
```or whatever it may be to```
Driver "vesa"
```

Save the file (Ctrl+O) and exit (Ctrl+X).

Then restart X using Ctrl+Alt+Backspace (not Delete, this doesn't restart the PC, just the X server)


If you get into Ubuntu, then you are halfway there.  Those "vesa" drivers are just the quick fix.  You should look into installing the ATI drivers.

You can try either this HOWTO

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)

[Ubuntu Forums - Easy Ubuntu v2.2](http://ubuntuforums.org/showthread.php?t=64629)

---

### Post by Darkness on 2006-03-27
[QUOTE=Sutekh]Okay you need to change the driver that X is currently using.

First backup and edit the X configuration file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```
 - When prompted for a password use your user's password

 - Those commands are case sensitive so make sure its X11 not x11 (or just copy and paste the commands)


When the file opens move down until you reach the section entitled
```
Section "Device"
```
Change the line that contains
```
Driver "ati"
```or whatever it may be to```
Driver "vesa"
```

Save the file (Ctrl+O) and exit (Ctrl+X).

Then restart X using Ctrl+Alt+Backspace (not Delete, this doesn't restart the PC, just the X server)


If you get into Ubuntu, then you are halfway there.  Those "vesa" drivers are just the quick fix.  You should look into installing the ATI drivers.

You can try either this HOWTO

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)

[Ubuntu Forums - Easy Ubuntu v2.2](http://ubuntuforums.org/showthread.php?t=64629)[/QUOTE]

Well, this was the way to fix my problem.  Now, I can use the GUI to find my other ATI drivers which will be a lot easier than trying to master the shell prompt right off the bat!

Thank you so much!

---

### Post by Sutekh on 2006-03-27
[QUOTE=Darkness]Well, this was the way to fix my problem.  Now, I can use the GUI to find my other ATI drivers which will be a lot easier than trying to master the shell prompt right off the bat!

Thank you so much![/QUOTE]
No problem.

The two link I posted give you the option of installing the ATI drivers through a terminal window (in X so its not like the command line for real, you can have music playing in the background :)) or through a GUI.

If you are okay with terminal (and its pretty easy) then follow the UDSF link

If you want the GUI then install EasyUbuntu to get the ATI drivers.

---


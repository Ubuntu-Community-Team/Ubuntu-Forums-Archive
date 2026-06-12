---
title: "My BIG MP3 Player Mystery KDE vs. GNOME"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-02-16
I am using Edgy. When I connect my MP3 player under Gnome it says it is 25% full (that is right!!!) But when I go to transfer music it says "device is full". At first it puzzled me that I could only use my Windows partition with this player. But now I have set up KDE and everything works fine. 

Why did GNOME have problems with the player. Truth be told I like GNOME better, but KDE seems more reliable.

Also how do I access Nautilus and the Gnome Wifi utility under KDE. Is it possible?

Thanks

---

### Post by jordanmthomas on 2007-02-16
```
nm-applet --sm-disable
```
for the wireless utility
```
nautilus
``` to run nautilus

make launchers or whatever you want to do

---

### Post by Arisna on 2007-02-16
I don't know what the cause of it is, but I have noticed that KDE and Gnome handle removable media rather differently.  As to Nautlius and the Gnome Wifi utility, you can add them to your KMenu if you know the commands for them (for Nautlius, it is "nautilus").  However, there are good KDE alternatives available--you can install Dolphin if you don't like Konqueror, and kubuntu-desktop ships with Wifi utils if I remember correctly.

---

### Post by scwinn on 2007-02-16
Sorry I am a serious Newbie.... so could you be more specific about nm-applet --sm-disable and also the nautilus issue.

Thanks

---

### Post by jordanmthomas on 2007-02-16
To run the wireless applet, press Alt + F2
type
```
nm-applet --sm-disable
``` and it will pop up in your system tray.
do the same for nautilus
```
nautilus --no-desktop
``` is actually what you'll want to run so that KDE still manages your desktop.


To add a launcher in your kicker (taskbar, whatever you want to call it) right click and go to 'add application to panel' --> add non kde application

in the command section put one of the above commands.  Now, you can just click to launch them.


to make the wireless thing start when you log in, open up a terminal
```
nano ~/.kde/Autostart/wifi
```
post this in there:
```
#!/bin/bash
nm-applet --sm-disable
```
Ctrl-X,Y,Enter to save
then
```
chmod +x ~/.kde.Autostart/wifi
```
Then, it will be started when you log in.


**for the record, I have no idea what the --sm-disable switch does, but everywhere I have seen shortcuts to the network manager applet, it is there.

hope this clears things up a *little* bit

---

### Post by scwinn on 2007-02-16
Does KDE have a similar network applet. My Internet goes down a lot and I have to reconnect.

---

### Post by jordanmthomas on 2007-02-16
knewtorkmanager is kde's version

---


---
title: "Screen Resolution"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by nsmith on 2006-03-31
I cannot change the screen resolution it is currently set at 640 by 480 pixels.  It was not always so.  I brought my computer to work to try and install a few things and I still get good resolution at work 1024 by 768 but when I take my computer to my home the resolution is 640 by 480 without the option to change.  Any ideas?

---

### Post by jolger on 2006-03-31
maybe your screen doesn't support any other resolutions...

although that seems a bit unlikely...

---

### Post by nsmith on 2006-03-31
My screen does support other resolutions.  It was origianlly set at 1024 by 768.  I took it into work installed a few things and now when I take it back to my home the resolution is set 640 by 480.

---

### Post by Ubuntuud on 2006-03-31
You could edit your xorg.conf

Do: "sudo gedit /etc/X11/xorg.conf", in a terminal (without the "").

Go to the section where all the resolutions are and change them to the desired one.

If those are already set to that resolution, I am afraid it's beyond my reach.

---

### Post by Gustav on 2006-03-31
Try typing this in the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the instructions.

edit: It can be smart to back up /etc/X11/xorg.conf in case you do something wrong :)

---

### Post by Mustard on 2006-03-31
Try this...

ctrl + alt + f1 to get to a terminal (remember that you can use ctrl + alt + f7 to get back to desktop). Login with username and user password to get a command prompt

```
sudo /etc/init.d/gdm stop
#shutdown gnome desktop manager
```

```
sudo dpkg-reconfigure xserver-xorg
#reconfigure xorg.conf
```

Choose the default answers for whatever things you don't know the answers to.  When you get to the screen resolutions dialog, add the screen resolutions you want.  When you finish answering all the questions it will make a backup of your old xorg.conf and name it according to the date and time it was made.  It will then write a new copy of your xorg.conf according to the choices you made in the configuration dialog.

Then do this..

```
startx
#restart the Xserver
```

if startx doesnt work try this..

```
sudo /etc/init.d/gdm restart
#restarts the gnome-desktop-manager
```

Check to see if your new resolution settings are working.

If you still have issues visit this thread...

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---


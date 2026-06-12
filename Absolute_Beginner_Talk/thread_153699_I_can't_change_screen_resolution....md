---
title: "I can't change screen resolution..."
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by StraightToPlaid on 2006-04-01
I just did a fresh install of ubuntu on my older desktop and it's my first experience with Linux, so please bear with me, I'm a bit new at this.

After I finished installing it loaded in 640x480, and when I went to system>preferences>change screen resolution the only option it gives is 640x480.  I tried installing nvidia's drivers for my card, following the help file and I was succesful I think, I can now go into the drivers for my card and change the brightness, color balance and stuff like that so I think the drivers are working fine.

What else should I try?

---

### Post by StraightToPlaid on 2006-04-01
I just realized that giving you my video card might help.  I'm running a geforce 4mx 420.  Yeah, I know, old hardware, but this is my old desktop.

---

### Post by Mustard on 2006-04-01
Try reading over this link and see how you go....
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

These are the instructions that I copy and paste for this on occasion, they are not that much different from the link above, but the link above goes into more detail.

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

### Post by BoneKracker on 2006-04-01
If the Debian configuration utilities aren't providing optimimal settings for your hardware, you may want to manually tweak some of the X-windows settings, which are managed in the configuration file:

**/etc/X11/xorg.conf**

First, it may be useful to read the man page that provides documentation of the Xorg X11 configuration file.  From the terminal, type:

```
man xorg.conf
```

Some specific areas of the file you should pay attention to are the sections:
1. Section "Device" (which should reflect the graphics card you are using).
2. Section "Monitor" (make sure the horizontal and vertical refresh rates are correct for your monitor; refer to the manual that came with the monitor or look them up on the internet)
3. Section "Screen" (There should be a "Display" subsection for each bit-depth you may want to use (e.g., Depth 8, Depth 16, Depth 24)), and in each of these subsections, _there should be a list of "Modes" (video resolutions which you may want to use - e.g., "1600x1200" "1280x1024" "1024x768" "800x600" "640x480")._  I would list the ones that the monitor's manual suggests as supported modes for the monitor (although it will probably be able to do others).

---


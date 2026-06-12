---
title: "Resolution Problem"
date: 2007-04-02
forum: Apple Intel Users
---

### Post by Weebs on 2007-04-02
I've currently got Ubuntu Linux 6.10 installed and running very well on my Intel iMac 17" (Core Duo). The only problem right now is that I can't figure out how to get my resolution past 1024x768, and my default resolution is 1440x900. I found a few threads with the same issue, but none of the fixes seemed to work for me. :confused:

---

### Post by Chrisj303 on 2007-04-03
Follow this guide : [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Towards the ends there is instructions on getting 915resolution - that'll sort you out!

chrisj303

---

### Post by cyberdork33 on 2007-04-03
Please post back if that works... It was my understanding that 915resolution does not work with the iMac, just the MacBooks. (Different video devices)

OK, after looking a bit, there are different video devices for the 17" iMac. some have Intel graphics... other have ATI Graphics

---

### Post by Weebs on 2007-04-03
After installing 915resolution via apt-get, it told me it was unable to start. It said I needed and intel 800/900 chipset, and I'm assuming this is because my iMac has a ATi X1600

---

### Post by cyberdork33 on 2007-04-03
Have you installed the fglrx driver?

---

### Post by Weebs on 2007-04-03
EDIT: I've gotten fglrx installed, and now my resolution is at my screens native 1440x900 and it looks GREAT :). The only problem is that I was unable to get 3D Acceleration working, I tried using [this](http://wiki.cchtml.com/index.php/Troubleshooting#No_3D_acceleration) method to fix it, but I'm still only getting

```
display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: www.mesa3d.org 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

Whenever I try the fglrxinfo command. My iMac has a ATi Radeon Mobility X1600 (128MB)

---

### Post by cyberdork33 on 2007-04-04
Make sure you have the following in your xorg.conf:

```
Section "Device"
...
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "KernelModuleParm" "aglock=0"
...
EndSection
```

Be sure to completely restart X (or just reboot)

---

### Post by Richard777 on 2007-04-04
hey i was wondering if u guys can help me out here. iv'e just installed ubuntu and when i try to boot it, my screen says it cannot display anything blah blah...i don't know what to do. please help a no0b

---

### Post by cyberdork33 on 2007-04-04
> hey i was wondering if u guys can help me out here. iv'e just installed ubuntu and when i try to boot it, my screen says it cannot display anything blah blah...i don't know what to do. please help a no0b

Are you on an Intel Mac? This is the Intel Mac forum. You should probably start your own thread, and you will have to give more information than what you just posted... blah blah blah is not helpful for us to understand a problem.

---

### Post by Seamyst on 2007-04-15
Doing the terminal commands as given in the HowTo guide didn't work - it said that part of the command was unknown.  But if you go into Synaptic Package Manager and search for "915Resolution", it'll bring up the one package you have to install.  Do Ctrl-Alt-Delete to log out and back in, and it's good to go.  The resolution was set to the default for my OS X partition automatically.

Yayy!!

---

### Post by cyberdork33 on 2007-04-17
> **Seamyst said:**
> Doing the terminal commands as given in the HowTo guide didn't work - it said that part of the command was unknown.  But if you go into Synaptic Package Manager and search for "915Resolution", it'll bring up the one package you have to install.  Do Ctrl-Alt-Delete to log out and back in, and it's good to go.  The resolution was set to the default for my OS X partition automatically.

Yayy!!

You only use the 915Resolution Package for Macs with Intel Graphics

---

### Post by sc00ter on 2007-05-04
I recently had a similar issue with my Radeon X1600 PRO (using the restricted drivers),  my external video display is an LCD TFT monitor.

Initially I couldn't get resolutions any higher than 1024x768. After adding the resolution of 1280x1024 to my xorg.conf, rebooting would not not display anything.

Hitting CTRL+ALT+F1 and removed (commented out) the following 2 lines from the **"Montor" section** within **/etc/X11/xorg.conf**:

HorizSync ...
VertRefresh ...

Restarted the GDM and now I have my display back with the higher resolution of 1280x1024.


*n00b stuff (saves goggling around):

To edit xorg.conf within tty, use the following:

**sudo nano /etc/X11/xorg.conf**

To restart GDM from the tty:

**sudo /etc/init.d/gdm restart**

---


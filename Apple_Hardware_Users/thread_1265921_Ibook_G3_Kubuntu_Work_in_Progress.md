---
title: "Ibook G3 Kubuntu Work in Progress"
date: 2009-09-14
forum: Apple Hardware Users
---

### Post by rjcalifornia on 2009-09-14
This a small tutorial on how to install Kubuntu 9.04 on an ibook G3. This is a work in progress, so if you encounter a problem, post it here, may be someone can help. 

DISCLAIMER:

This is a guide to help beginners.

Tested on iBook G3. 500 MhZ. 640 MB RAM. 8 MB VRAM and Dual Boot Mac OS X.

Keyboard-Works
Keyboard Brightness/Volume Control- Works
Screen-Works
Sleep-Works (doesn't sleep when closed. must select from menu.)
USB-Works
Firewire-Works
Ethernet-Works
Sound-Works
Mic-Works (out of the box, no need to install something else)
WiFi-N/A
Trackpad-Works (fn +F12 for right-click)
Eject CD - Works (Need to run the command 'eject' on Terminal)


How to install?

Download the live cd version of Kubuntu from here:

[http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/)

When burning, be sure to burn it at 24x, this will prevent wasting of cd's.

After burning the cd, boot your iBook from it.(Press C after you hear the startup chime.


Press TAB key, and type this:

```
live-nosplash-powerpc
```

then, wait 'til the desktop appears (it is gonna take a while so, be patient) After the desktop is fully loaded, click on 'Install' and go through with the installation process. 

Reboot.

INSTALLATION:

Ok, now, the screen is messed up. To fix it, follow this steps....

Open 'Terminal' and type this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

This is to create a backup of xorg.conf, just in case something goes wrong.

After you have a backup of xorg.conf, type the following on 'Terminal':

```
sudo kate /etc/X11/xorg.conf
```

and replace what's there with this:

```
Section "Device"
Identifier "ATI Rage 128"
Driver "r128"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```

Save it, and then close Kate. Now, go to 'Terminal' and type this:

```
sudo ybin -v
```

After that, restart the ibook. No, no logout, restart. If the ibook does not restart, just "turn it off manually". Turn it on again and you'll have a working Kubuntu.

PROGRAMS AND UPDATES:

/*********************Xine***************************/

Xine is a powerful video player. To install it, open Terminal and type this:

```
sudo apt-get install xine-ui
```

/*********************XMMS2***************************/

Powerful and versatile music player. However, it does not come a graphical interface.

In 'Terminal', type the following:

```
sudo apt-get install xmms2
```

then:

```
sudo apt-get install esperanza
```

/*********************UPDATING***************************/

The Update Manager for some reason didn't work for me. So, type this in terminal:

```
sudo apt-get upgrade
```

It will install all the updates available.


That's it... Any questions, just hit the "Quick Comment" button...

---

### Post by zerobotman on 2009-09-14
> **RandyVanBuren said:**
> This a small tutorial on how to install Kubuntu 9.04 on an ibook G3. This is a work in progress, so if you encounter a problem, post it here, may be someone can help. 

DISCLAIMER:

This is a guide to help beginners.

Tested on iBook G3. 500 MhZ. 640 MB RAM. 8 MB VRAM and Dual Boot Mac OS X.

Keyboard-Works
Keyboard Brightness/Volume Control- Works
Screen-Works
Sleep-Works (doesn't sleep when closed. must select from menu.)
USB-Works
Firewire-Works
Ethernet-Works
Sound-Works
Mic-Works (out of the box, no need to install something else)
WiFi-N/A
Trackpad-Works (fn +F12 for right-click)
Eject CD - Works (Need to run the command 'eject' on Terminal)


How to install?

Download the live cd version of Kubuntu from here:

[http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/)

When burning, be sure to burn it at 24x, this will prevent wasting of cd's.

After burning the cd, boot your iBook from it.(Press C after you hear the startup chime.


Press TAB key, and type this:

```
live-nosplash-powerpc
```then, wait 'til the desktop appears (it is gonna take a while so, be patient) After the desktop is fully loaded, click on 'Install' and go through with the installation process. 

Reboot.

INSTALLATION:

Ok, now, the screen is messed up. To fix it, follow this steps....

Open 'Terminal' and type this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```This is to create a backup of xorg.conf, just in case something goes wrong.

After you have a backup of xorg.conf, type the following on 'Terminal':

```
sudo kate /etc/X11/xorg.conf
```and replace what's there with this:

```
Section "Device"
Identifier "ATI Rage 128"
Driver "r128"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```Save it, and then close Kate. Now, go to 'Terminal' and type this:

```
sudo ybin -v
```After that, restart the ibook. No, no logout, restart. If the ibook does not restart, just "turn it off manually". Turn it on again and you'll have a working Kubuntu.

PROGRAMS AND UPDATES:

/*********************Xine***************************/

Xine is a powerful video player. To install it, open Terminal and type this:

```
sudo apt-get install xine-ui
```/*********************XMMS2***************************/

Powerful and versatile music player. However, it does not come a graphical interface.

In 'Terminal', type the following:

```
sudo apt-get install xmms2
```then:

```
sudo apt-get install esperanza
```/*********************UPDATING***************************/

The Update Manager for some reason didn't work for me. So, type this in terminal:

```
sudo apt-get upgrade
```It will install all the updates available.


That's it... Any questions, just hit the "Quick Comment" button...

that's awesome! especially all the software!

---

### Post by zanyjazz on 2009-11-13
I am having trouble changing the Ubuntu window from 800x600.I have an iMac with a 24" screen and a ATI Radeon HD2600 Pro chip. Can you provide the code I need to change the display?

---


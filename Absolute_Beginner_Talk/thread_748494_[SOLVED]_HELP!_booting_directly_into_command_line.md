---
title: "[SOLVED] HELP! booting directly into command line"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by browny254 on 2008-04-07
Help...I just restarted and all is looking good for the start up procedures until I get to the login stage, its all command line based.

This is what I get on the display:
```
Starting up ...
[   16.146365] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0           (this usually happens and it works fine, its everything from now that I havent seen before)
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
kinit: name_to_dev_t(/dev/disk/by-uuid/1bdecd2d-4120-8ee3-a3e6-2ca2b4ff8191) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/1bdecd2d-4120-8ee3-a3e6-2ca2b4ff8191
kinit: No resume image, doing normal boot...

Ubuntu 7.10 andrew-laptop tty1

andrew-laptop login:

```

Im running Kubuntu here also so I dont know why it says Ubuntu.

I am able to log in and navigate fine and everything works, its just I have no idea what to do or where to even look. I tried booting up firefox and get this

```
(firefox-bin:5410): Gtk_WARNING **: cannot open display:
```


please help...ive just had to do a 3am mercy run into uni so i can get back to my assignment :P

---

### Post by bodhi.zazen on 2008-04-07
What error message do you get with this command ?

```
startx
```

---

### Post by browny254 on 2008-04-07
Thanks for the reply...I get a really big error message, Im using a different computer atm because i dont know if i can get on the net using command line

the last line says this though
```
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.
```

there was more than a whole screen of errors...I can try typing it all out if it will help...just not sure how to scroll up and see what happened first thats all...

---

### Post by pseudo-random on 2008-04-07
Can you show us your X server log please:
```
cat /var/log/Xorg.*
```

---

### Post by browny254 on 2008-04-07
Im not sure how to get it from my laptop (which is having the error) this this comp without typing it...I tried accessing the X server log and got a couple of screen of info before finishing with 

```
Fatal server error:
Requested Entity already in use!
```

is there anything i should look for in it? im not sure how else i can get the info across to you

---

### Post by pseudo-random on 2008-04-07
Ok lets filter it with```
cat /var/log/Xorg.* | grep EE
```
This will return only the lines with errors.
Just type the most interesting ones up here.

---

### Post by browny254 on 2008-04-07
```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
```

thats all i get...?

---

### Post by browny254 on 2008-04-07
oh yeah, i forgot to say in my first post that the Kubuntu splash screens work fine when starting up and shutting down, so the problem is between them somehow.

---

### Post by browny254 on 2008-04-07
ok i did this

```
sudo dpkg-reconfigure xserver-xorg
```

and its now working, except my max resolution is tiny, it wont go above 1024x768 (it also has a refresh rate of 85hz, i cant remember for sure but i think it only used to be 60hz...and it wont let me change that either)

ive tried searching a few other threads but cant find anything so if someone can point me in the right direction or just tell me how to do it that will be great.

---

### Post by tangibleorange on 2008-04-07
> **browny254 said:**
> ok i did this

```
sudo dpkg-reconfigure xserver-xorg
```

and its now working, except my max resolution is tiny, it wont go above 1024x768 (it also has a refresh rate of 85hz, i cant remember for sure but i think it only used to be 60hz...and it wont let me change that either)

ive tried searching a few other threads but cant find anything so if someone can point me in the right direction or just tell me how to do it that will be great.

can you remember which driver you selected when you reconfigured your X server?

Also, could you post the output of:

```
cat /etc/X11/xorg.conf
```

---

### Post by Therion on 2008-04-07
Here's what I had to do to correct that problem.  Using gedit, open your xorg.conf file: ```
gksudo gedit /etc/X11/xorg.conf
```
Accept the default settings for everything (use your Tab key to move through the menus) until you get to the section that deals with monitor resolution.

Going by memory here, but I think you'll see a window with some common monitor resolutions in it. Selected resolutions will be really low ones (480x600, 600x800 etc.) and have something that looks like:[*] to indicate they have been "selected". These are your available resolutions, and most likely they all suck. 

Thing is, this window only shows you some of the available resolutions. You can scroll up to get to more reasonable resolutions (1024x768, 1440x900 and so forth). The HIGHEST resolution you choose here will be the new DEFAULT resolution. So, bearing that in mind, remove the "*" from the crappy resolutions (use the space bar to remove it), and turn on three "good" resolutions by putting an "*" in those higher resolutions.  Save/overwrite and reboot if necessary.

---

### Post by browny254 on 2008-04-07
I think i just selected generic...i didnt change any default settings except the one to choose the resolution. i had a look in the monitor and display system settings though and it has "nv" for driver.

here is the output you asked for...

```

$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

---

### Post by tangibleorange on 2008-04-07
Where did you see "nv" for the driver? In this file, it says "vesa" is being used, which is the most basic driver (which probably explains the minimum resolution). Try:

```
sudo dpkg-reconfigure xserver-xorg
```

and on the first screen (or maybe second) select "nv" for the driver. Then, when it's finished, restart X by holding down Ctrl, Alt and Backspace.

---

### Post by browny254 on 2008-04-07
> **Therion said:**
> Here's what I had to do to correct that problem.  Using gedit, open your xorg.conf file: ```
gksudo gedit /etc/X11/xorg.conf
```
Accept the default settings for everything (use your Tab key to move through the menus) until you get to the section that deals with monitor resolution.

Going by memory here, but I think you'll see a window with some common monitor resolutions in it. Selected resolutions will be really low ones (480x600, 600x800 etc.) and have something that looks like:[*] to indicate they have been "selected". These are your available resolutions, and most likely they all suck. 

Thing is, this window only shows you some of the available resolutions. You can scroll up to get to more reasonable resolutions (1024x768, 1440x900 and so forth). The HIGHEST resolution you choose here will be the new DEFAULT resolution. So, bearing that in mind, remove the "*" from the crappy resolutions (use the space bar to remove it), and turn on three "good" resolutions by putting an "*" in those higher resolutions.  Save/overwrite and reboot if necessary.


ok i got a problem here...i dont have gksudo installed and when i try i get this

```

$ sudo apt-get -f install gksu
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  j2re1.4-mozilla-plugin: Depends: j2re1.4 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by tangibleorange on 2008-04-07
> **browny254 said:**
> ok i got a problem here...i dont have gksudo installed and when i try i get this

```

$ sudo apt-get -f install gksu
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  j2re1.4-mozilla-plugin: Depends: j2re1.4 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

In KDE, use this command:

```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by browny254 on 2008-04-07
> **tangibleorange said:**
> Where did you see "nv" for the driver? In this file, it says "vesa" is being used, which is the most basic driver (which probably explains the minimum resolution). Try:

```
sudo dpkg-reconfigure xserver-xorg
```

and on the first screen (or maybe second) select "nv" for the driver. Then, when it's finished, restart X by holding down Ctrl, Alt and Backspace.

ok that worked.

i saw the "nv" in a graphical systems setting area, kinda like the control panel area on windows. im running kubuntu so i think its slightly different to ubuntu.

i just restarted and i still started in command line mode and had to use startx to launch kubuntu...any ideas how to make it load the gui login screen instead?

---

### Post by bodhi.zazen on 2008-04-07
> **tangibleorange said:**
> Where did you see "nv" for the driver? In this file, it says "vesa" is being used, which is the most basic driver (which probably explains the minimum resolution). Try:

```
sudo dpkg-reconfigure xserver-xorg
```

and on the first screen (or maybe second) select "nv" for the driver. Then, when it's finished, restart X by holding down Ctrl, Alt and Backspace.

> **browny254 said:**
> ok i got a problem here...i dont have gksudo installed ...

<clip>

KDE uses kdesu (not gksu)

---

### Post by tangibleorange on 2008-04-07
what happens if you type:

```
cat /etc/init.d/kdm
```

---

### Post by browny254 on 2008-04-07
hmm...i just restarted again and eveything is back to normal.

thanks for your help guys, I was really stressing out when all this happened.

---

### Post by tangibleorange on 2008-04-08
> **browny254 said:**
> hmm...i just restarted again and eveything is back to normal.

thanks for your help guys, I was really stressing out when all this happened.

Not a problem! Please remember to mark the thread solved. It's under thread tools at the top of the page!

---


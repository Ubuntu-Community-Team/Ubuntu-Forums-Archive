---
title: "Nvidia GeForce FX 5500 Help!"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by izizzle on 2007-06-04
Hello everyone! I have a major problem now. I have an Nvidia Geforce FX 5500 graphics card which ubuntu does not install successfully. I have tried many attempts to install the driver, and it tells me to restart, but when I restart, it says that the x server could not load, and it brings me to this text mode screen. I do not know how to get back into graphical mode, so I have to reinstall Ubuntu every time I try to install the driver!

PLEEZ HELP!

---

### Post by igknighted on 2007-06-04
> **izizzle said:**
> Hello everyone! I have a major problem now. I have an Nvidia Geforce FX 5500 graphics card which ubuntu does not install successfully. I have tried many attempts to install the driver, and it tells me to restart, but when I restart, it says that the x server could not load, and it brings me to this text mode screen. I do not know how to get back into graphical mode, so I have to reinstall Ubuntu every time I try to install the driver!

PLEEZ HELP!

Very simple, when it takes you to a CLI, you simply log in and type:
```
sudo dpkg-reconfigure xserver-xorg
```
then answer the questions, choosing 'nv' as the driver, not nvidia.

**NOW, for installing the driver:**

Assuming you are on a fresh install, try opening a terminal and typing:
```
 sudo apt-get update
sudo apt-get install nvidia-glx-new
```
Then open the xorg.conf file manually like this:
```
gksudo gedit /etc/X11/xorg.conf
```
Once you have it open, scroll to the section "Device" and there should be a line that reads:
> driver "nv"
change it to:
> driver "nvidia"
then save the file, and restart X with ctrl-alt-backspc

NOTE: This is the manual method, but since the automatic method failed, try this instead.

---

### Post by izizzle on 2007-06-04
I LOVE YOU! It worked! However, the windows no not have the top bar where the X button is to close the window. And I cannot move the windows. P.S- Do you know the keys to push for the cube? thanks in advance izizzle

---

### Post by igknighted on 2007-06-04
> **izizzle said:**
> I LOVE YOU! It worked! However, the windows no not have the top bar where the X button is to close the window. And I cannot move the windows. P.S- Do you know the keys to push for the cube? thanks in advance izizzle

Open the xorg.conf file in the same way as above, then find the section "Screen".  Add a line right before the EndSection line that reads like this:
```
Option "AddARGBGLXVisuals" "true"
```
then save/restart X

In the meantime you can move windows around by hold alt and clicking/dragging anywhere in the window.

middle button click on the desktop lets you drag the cube around, ctrl+alt+click does as well.  ctrl-alt-rightarrow moves the cube right, and left does likewise move it left.  Play around in the settings manager to learn some fun stuff.

---

### Post by izizzle on 2007-06-04
Hmmmmm. I got the bar problem fixed, but i still cant seem to rotate the cube...Any ideas...I have it enabled

btw, I have the scroot button for a middle button on my mouse.And, how do I get to the settings manager for the desktop effects?

---

### Post by Klaidas on 2007-06-13
I've noticed your PC setup is pretty similar to what I have... any chances your motherboard uses AGP version 2.0 2x/4x? 

I was wondering if I could use that GeForce FX 5500, which is AGP **3.0** 8x/4x/2x/1x in that older AGP slot, as  I've heard speeds are backwards compatible, but how about the voltage that is needed for that FX 5500? Is it 0.8V, 1.5V or can it run both?

---

### Post by izizzle on 2007-06-13
How do I find out what version of AGP my motherboard uses?

---

### Post by Klaidas on 2007-06-14
First, find out what motherboard you have. You can do that by opening the case and finding a sticker somewhere, or by using a diagnostics tool (on Windows you can use Everest or Aida32).

Then, you can find a manual for that motherboard on the internet :) It should state what AGP slot it uses.

---

### Post by kabotage on 2007-08-22
> **igknighted said:**
> Very simple, when it takes you to a CLI, you simply log in and type:
```
sudo dpkg-reconfigure xserver-xorg
```
then answer the questions, choosing 'nv' as the driver, not nvidia.

**NOW, for installing the driver:**

Assuming you are on a fresh install, try opening a terminal and typing:
```
 sudo apt-get update
sudo apt-get install nvidia-glx-new
```
Then open the xorg.conf file manually like this:
```
gksudo gedit /etc/X11/xorg.conf
```
Once you have it open, scroll to the section "Device" and there should be a line that reads:

change it to:

then save the file, and restart X with ctrl-alt-backspc

NOTE: This is the manual method, but since the automatic method failed, try this instead.

you rulz bro!!! :KS:KS:KS

thanks coz im really noob, like 4 days from windows to ubuntu!hehe..

and can i change my resolution other than 1024x768? make it higher? maybe? :confused:

---

### Post by igknighted on 2007-08-22
> **kabotage said:**
> you rulz bro!!! :KS:KS:KS

thanks coz im really noob, like 4 days from windows to ubuntu!hehe..

and can i change my resolution other than 1024x768? make it higher? maybe? :confused:

Open the xorg.conf file as above.

The find the section that looks like this:
```
Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        Option      "AddARGBGLXVisuals" "True"
        Option      "DisableGLXRootClipping" "True"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

Yours will have a buch of display subsections, each with a different Depth.  The default depth is probably 24 (it should be, if it isn't change it).  Then go to the subsection for depth 24 and there should be several modes listed.  "1024x768" will likely be the first.  Add "1280x1024" in front of it, separated by a space.  Then save & exit, and restart X.

---


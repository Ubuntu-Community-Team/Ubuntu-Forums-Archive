---
title: "Middle mouse button to be used as scroll."
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-28
On my thinkpad in windows, i can hold down the middle mouse button and move the mouse and it scrolls the document...  How do i configure gnome to do this? :-k :-k :-k :-k :-k

---

### Post by doclivingston on 2006-02-28
In general, you can't.

In X clicking the middle mouse button gets used to paste the current selection. Click-and-dragging the middle mouse button gets used by many apps for other things, such as bringing up the copy/move/link menu in Nautilus (equivalent to Window Explorer's right-click-drag).

---

### Post by BoyOfDestiny on 2006-02-28
Well if you mean in firefox, it's easy enough (I'm using 1.5 but it should be similar to this) 

Edit -> Preferences -> Advanced

General Tab

Use autoscrolling

---

### Post by IYY on 2006-02-28
Yep. And it's on by default in Galeon.

---

### Post by jimrz on 2006-02-28
Enable TrackPoint middle-button scrolling

To use the blue middle TrackPoint button as a scroll wheel (using the red TrackPoint itself to scroll up and down), do the following. In a terminal, enter these commands:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original
sudo gedit /etc/X11/xorg.conf

In the editor, find the section headed Section “InputDevice” / Identifier “Configured Mouse” and the following lines above the “EndSection” line:

Option    "EmulateWheel"        "true"
Option    "EmulateWheelButton"  "2"

Save the file. Logout, restart X with Ctrl-Alt-Backspace, and log in again.

Source for this item: Many ThinkPad-related sites, confirmed by experiment.

Copied from [[COLOR="Sienna"]**_this_**[/COLOR]]("http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#intro") excellent how-to. Works great on my T42 and contains lots of other good stuff and links to even more.

---

### Post by David Oxland on 2006-04-23
As mentioned in other peoples posts I've been to enable the autoscrolling in Firefox itself but not in any other document. Particularly frustrating for me is not having it in Evolution where these long mailing list fwds need to be scanned through. It would seem to have it be a function of the mouse rather than of the program
Hope this makes sense
David

---

### Post by SS2 on 2006-10-27
Hi,

> **jimrz said:**
> Copied from [[COLOR="Sienna"]**_this_**[/COLOR]]("http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#intro") excellent how-to. Works great on my T42 and contains lots of other good stuff and links to even more.

Thank you for this small how-to :)

It works fine on my T23. Really missed this feature: No scolling...

Greetings,
Simon

---

### Post by Tozzano on 2008-01-01
Thanks!

---

### Post by wwbkmd on 2008-02-01
Thanks for this! Very helpful :)

---

### Post by Atomjack Magazine on 2008-03-04
> **jimrz said:**
> Enable TrackPoint middle-button scrolling

To use the blue middle TrackPoint button as a scroll wheel (using the red TrackPoint itself to scroll up and down), do the following. In a terminal, enter these commands:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original
sudo gedit /etc/X11/xorg.conf

In the editor, find the section headed Section “InputDevice” / Identifier “Configured Mouse” and the following lines above the “EndSection” line:

Option    "EmulateWheel"        "true"
Option    "EmulateWheelButton"  "2"

Save the file. Logout, restart X with Ctrl-Alt-Backspace, and log in again.

Source for this item: Many ThinkPad-related sites, confirmed by experiment.

Copied from [[COLOR="Sienna"]**_this_**[/COLOR]]("http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#intro") excellent how-to. Works great on my T42 and contains lots of other good stuff and links to even more.

Worked perfectly the very first time on my X61 Tablet.  Which is nice, considering some of the other methods I tried fragged my xorg.conf file, and didn't work.  This one is much simpler too.  

Thanks.

---

### Post by BrandonG777 on 2008-04-09
Had some problems with this at first on my Thinkpad R40e running Hardy Heron. Try this if your having problems.

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "EmulateWheel"          "true"
        Option          "EmulateWheelButton"    "2"
EndSection


Without CorePointer the primary button acted very strange and I think the key was using the mouse driver instead of the synaptics driver. Of course I have a trackpoint anyway so not sure why I would even be using the synaptic driver unless they are made by synaptic.

---


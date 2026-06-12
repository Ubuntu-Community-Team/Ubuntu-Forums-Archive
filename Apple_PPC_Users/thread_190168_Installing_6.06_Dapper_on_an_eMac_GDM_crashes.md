---
title: "Installing 6.06 Dapper on an eMac GDM crashes"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by matt221984 on 2006-06-05
For those of you who might be trying to install dapper onto an eMac G4 and are having some problems with X or GDM crashing, here's what I did to be able to get into x to be able to install.

1) boot from the ubuntu powerpc cd and when yaboot loads press enter to boot using the default image

2) it may take a minute or so to load, eventually it will get to a blue screen with an error that says **"Failed to start the X server..."**, click NO.

Then you will be given an error that says **"The X server is now disabled. Restart GDM when it is configured correctly."**, click OK.

You will then be sent to a command line.

3) type **sudo pico /etc/X11/xorg.conf**

5) scroll down until you find the following text:

```
Section "Monitor"
           Identifier           "Generic Monitor"
           Option               "DPMS"
           HorizSync          28-51
           VertRefresh        43-60
EndSection
```

Change the HorizSync to **71-73**
Change the VertRefresh to **70-140**

6) press **CTRL+x** to quit, press **Y** to save, and press **ENTER** to overwrite the existing file.

7) type **startx**

If your situation is the same as mine was this should start X for you and you should be able to install Dapper.

This worked on an eMac that shows the following written inside the CD drive door

**G4 - 1.25GHz/256/40/combo/56k/110v**

It took me a couple hours to figure this out, so I thought I'd post it here for all of the n00bs like me.

---

### Post by markwren on 2006-06-29
In xorg.conf I needed to extend the horizontal sync range end:
   HorizSync 28-80
AND add extra resolution to the front of the resolutions lists "1024x768" "800x600" etc (you can get away with only doing it for the 24bpp stanza if you're feeling lazy):
   "1600x1200" 

The screen comes up perfectly, except, for me, it needed some tweaking using "xvidtune" in a terminal window to get it to fit inside the monitor properly.

Annoyingly there still seems to be no easy way to emulate a right-click with the Apple one-button mouse. And I couldn't find a way of jumping out of X to the 5 other virtual terminals you get from Alt-F1 to F5 on a PC.

But importantly Dapper DOES WORK ON AN EMAC, contrary to what you might find in other advice from searching Google.

---

### Post by xkiddiegrinders on 2006-06-29
This same thing happened to me but on my G4 Dual 450 AGP graphics tower. Your fix made it run thats for sure...

---


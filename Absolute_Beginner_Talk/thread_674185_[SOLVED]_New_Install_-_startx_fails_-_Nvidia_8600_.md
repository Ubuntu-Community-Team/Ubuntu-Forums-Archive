---
title: "[SOLVED] New Install - startx fails - Nvidia 8600 GT"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Cal55 on 2008-01-21
Hi All,

I'm struggling. I'm fairly new to Linux/Ubuntu.   I had a successful install of Gutsy on an old P4 1.4.  for about a fortnight till it suffered a fatal hardware fault.  Thus I'm trying to install Gutsy on a new PC, with no existing operating system.  The spec is :- Intel Core 2 Duo E6750, 2Gb RAM, Nvidia 8600GT, MSI P6NGM Mobo, ASUS VW193S 19" TFT.

Basically I can't get any version of the install to get beyond a command-line.   I've tried :-

1. 7.04 Feisty Live CD.  Failed with error 'bin/sh : can't access tty; job control turned off'.  Tried low graphics mode, no joy.

2. 7.10 Gutsy Desktop install (not live CD).  This stalled at 'Running local boot scripts (/etc/rc.local)'.  An Alt + F2 gives me a console.  But 'startx' gives 'Fatal Server Error: No screens found'.  I tried various of the suggested edits to /etc/X11/xorg.conf but feel I'm stabbing in the dark.  

3. 7.10 Gutsy Alternative install. This worked through the whole install, partitioning, localization, etc.  When asked to reboot it stalled at 'Running local boot scripts' as above.  Alt + F2 gives a console.  But after providing ID and Password,  'startx' gives :-
```

(WW) NV: No matching Device section for instance (BusID PCI:0:3:3) found
(WW) NV: No matching Device section for instance (BusID PCI:2:0:0) found
(EE)   No devices detected

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 events remaining

```
... sorry if any errors in the above.  I had to copy it as I don't know how to get files off the PC with only command line...

Thus.  I guess I've got a problem with the Graphics Card not being detected (properly) or not being able to use the default driver??  Does that seem correct?  

lspci suggests (to me) that the card is at 00.20.0, I think.  :-
```

...
00.10.0 VGA Compatible controller: nVidia Corporation Unknown device 07e1 (rev a2)
00.20.0 VGA Compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

```

 Although it does have two monitor connections, and the mobo has onboard graphics (with a connector I don't have).

Thus.  Is there any way to install the correct driver from the command line? - taking into account I have  little Linux command line knowledge, and no FDD.    (I can ping an external IP address though)

Any help would be much appreciated.

Cheers
Chris

---

### Post by tgalati4 on 2008-01-21
I've had a successful install with a similar system although it's a single monitor version of the 8600GT not a dual-DVI.  I used Linux Mint 4 (gutsy) with envy to load the lastest nVidia drivers.

Try turning off your onboard video card through the BIOS to see if it will load properly.

---

### Post by OffAxis on 2008-01-21
so you've got a working install now, and just no gui, correct?

have you tried 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will let you input some settings for your monitor and fill out those sections you're missing in xorg.conf (the device and related display).

the 'nv' driver should work for your 8600 gt.

---

### Post by gangrelsurf on 2008-01-21
What OffAxis says, but first I'd go to bios and disable that onboard card if you havn't already

---

### Post by Cal55 on 2008-01-21
WOW!!  Thanks guys!!  :)

Stopping the onboard chip didn't seem to help (did a reboot, but still failed as before).  Doing the 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

then startx

Has given me a gui.  Some odd effects, but I guess I'll sort them with the proper driver.  I was intending to try 'Envy' ??


BTW.  Can't work out how to mark this thread as SOLVED.  FAQ says something about radio buttons - I can't see them?

Cheers
Chris

---


---
title: "Screen Resolution on B&amp;W G3"
date: 2008-12-13
forum: Apple Hardware Users
---

### Post by GavoKaotik on 2008-12-13
Hi all!

After thinking about it a lot, I installed Ubuntu 8.04.1 to my Power Mac B&W G3 (Rev1), here are its specs:

- PowerPC G3 @ 350 Mhz
- 640 MB RAM
- 2 x 6 GB HDD (one HD is Ubuntu, the other is my old OS9 archive ^^)
- ATi Rage Pro 128 MB
- 17" VGA Monitor

It used to had Mac OS X 10.3 and the maximum resolution was of 1280x960, but with Ubuntu it only gives me he option of 800x600. Any ideas? 'Cause that resolution isn't nice AT ALL! :confused:

---

### Post by stream303 on 2008-12-14
Awesome - you are 90% home.

What are the specs for your external monitor, ie the vertical and horizontal frequency ranges?  Whatever you do, save your existing /etc/X11/xorg.conf file as a backup.

Then, you may want to edit/change/add in these values:  (gksudo gedit /etc/X11/xorg.conf, or in a terminal sudo nano /etc/X11/xorg.conf)

CHANGE the horizontal and vertical freqs to match those of your own monitor's specs!

```

Section "Monitor"
   Identifier  "Configured Monitor"
   HorizSync   30-87
   VertRefresh  50-85
EndSection

Section "Screen"
   Identifier  "Default Screen"
   Monitor     "Configured Monitor"
   Device      "Configured Video Device"
   DefaultDepth   24
     SubSection     "Display"
     Depth          24
     Modes         "1280x960"
     EndSubSection
EndSection
```

Do NOT put quotes around either of the Depth values..

...+ more of your existing xorg.conf...

CHANGE the vertical and horizontal freqs to match the specs of your monitor!  Log out and log back in to see the change, or simply reboot.

If you can't find your monitor specs, post what it is and maybe we can help find them....

---

### Post by GavoKaotik on 2008-12-14
Hi, thanks for answering ^^

I set the values for the Screen section just like your example and it's still on 800x600 (I didn't wanted to try the HorizSync and VertRefresh 'cause I don't know those values for my monitor).

I can't find anything about those 2 values for my monitor. It's a **Likom ViewMate Oz795G3**, and the max resolution should be 1600x1200 O.o

---

### Post by linux_tech on 2008-12-14
There are 2 ways I know of to adjust monitor settings; either by editing xorg.conf or by using xrandr.  I like xrandr because it is dynamic, faster to troubleshoot and usually resolves issue faster.   

I usually start by going to terminal and typing in
```
xrandr
```
This should give you information such as; 
the available resolutions for all connected monitors 

To set resolution to 1280x960, you may try
```
xrandr --output LVDS --mode 1280x960
```

```
xrandr -s 1280x960 
``` or whatever resolution[/code]

---

### Post by GavoKaotik on 2008-12-14
I got a bigger resolution: 1024x768!!! Modifying the xorg.conf file. With xrandr, it listed as the bigger resolution 800x600, and couldn't make it bigger that way.

However, it only seems to work with 1024x768... When I put 1280x960 in my xorg.conf, the screen looks somewhat "narrowed", and the Screen Resolution panel list 1280x800 and 1280x768 (at least I think that the last one was that), not 1280x960... and if I let it on 1024x768 with my xorg.conf file saying 1280x960, glxinfo and glxgears throw a Segmentation Fault.

Any ideas?

---

### Post by stream303 on 2008-12-15
The key is to find out what the monitor's specs are - I have tried searching, but couldn't find any specs beyond just using 60hz for that Likom.

Since that is a crt, just know that they are much more likely to be damaged by incorrect video freqs than an lcd panel, so you may end up replacing it sooner than later. :(

1024x768 is probably good for now, but even then you may be stressing the monitor with freqs outside the range it is designed for.  We just don't know until the specs are found.

If that Mac is really important, you may want to consider finding a monitor replacement with known specs.

---


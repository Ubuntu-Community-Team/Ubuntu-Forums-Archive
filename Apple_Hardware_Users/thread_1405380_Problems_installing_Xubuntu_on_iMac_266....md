---
title: "Problems installing Xubuntu on iMac 266..."
date: 2010-02-12
forum: Apple Hardware Users
---

### Post by StivVid on 2010-02-12
Hi, all.

I'm very much a newbie to Linux and am hoping to breathe new life into an old iMac by installing Xubuntu.  I've tried every type of installation I can think of, and nothing has worked so far.  A little background on the machine...  It's a lime green iMac 266 with 160 MB of ram and a 120 GB hard drive.  Because of the low memory on my system, I've been trying to use the alternate install CD for Xubuntu 9.10.  Everything seems to go fine until I reach the point where it's time to boot the system for the first time.  Machine starts to boot...  I see the little mouse, then a few minutes later the monitor shuts off and I'm looking at a black screen.  The hard drive keeps making noise like it's still trying to boot up, but nothing happens...  only darkness.  (Sniff, sniff.)  Please help me if you can.

---

### Post by oswaldkelso on 2010-02-13
[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank) screen on iMac G3

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

On a 226 with 160mb you'd be better building a lighter system. I'd suggest you put up with the slowness while you learn then re-build

Don't bother with gnash or swdec for flash on that low-end system use clive or abby.
 
```
cclive -s youtube-video-url 
```

to play youtube  in your favorite player

Spend some time reading up, lots of tip in my sig

---

### Post by linuxopjemac on 2010-02-13
you have to edit your /etc/X11/Xorg.conf file.

In a terminal (try to boot a rescue mode) and then you edit with

sudo nano /etc/X11/Xorg.conf

and paste the following lines there:
```

##imac-ppc-tray-loader-xorg.conf###

   
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:lwin_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
EndSection

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:18:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
EndSection

Section "Module"
Disable "glx"
Disable "dri"
EndSection
######end########
```

then CTRL-X to exit, then "y" to save the changes.

then reboot and boot into linux.

---

### Post by StivVid on 2010-02-13
I was thinking the system might be pretty sluggish.  Anyway...  thought I'd try it out to see if I like it.  If I do, I'll be maxing out the ram at 512 MB.  Would Xubuntu's performance be respectable after the upgrade?  (Compared to OSX on the same machine?)

---

### Post by StivVid on 2010-02-14
OK.  I followed all the instructions from the wiki.  I'm installing from the Ubuntu alternate install cd in command line mode.  I get all the way to the step where I enter startx, and then the monitor shuts off and I'm left with a black screen again.  When I try the next step, CTL+ALT+Backspace (I'm assuming that means delete on a mac keyboard.) nothing happens.  I can bring the monitor back up by pressing CTL+ALT+F1 and then I get some error messages and just a flashing cursor.  The command prompt never returns and I have to do a hard shut-down and restart the computer.  Help!

---

### Post by StivVid on 2010-02-14
I'll try linuxopjemac's suggestion next.  Fingers crossed...

---

### Post by StivVid on 2010-02-14
You're a genius, linuxopjemac!  Worked like a charm.  Thanks a million!  Now I've got to order more ram.

---

### Post by oswaldkelso on 2010-02-14
> **StivVid said:**
> OK.  I followed all the instructions from the wiki.  I'm installing from the Ubuntu alternate install cd in command line mode.  I get all the way to the step where I enter startx, and then the monitor shuts off and I'm left with a black screen again.  When I try the next step, CTL+ALT+Backspace (I'm assuming that means delete on a mac keyboard.) nothing happens.  I can bring the monitor back up by pressing CTL+ALT+F1 and then I get some error messages and just a flashing cursor.  The command prompt never returns and I have to do a hard shut-down and restart the computer.  Help!

Out of curiosity did you have the original imac keyboard? I seem to remember having to plug in a standard usb keyboard to get past that error on some releases. If the Keyboard gets mapped wrongly you can't make the changes to fix it. A swap keyboard and reboot, may have been all that was required. Also NOT selecting the mac keyboard on install may work.

---

### Post by linuxopjemac on 2010-02-15
great work!

---

### Post by StivVid on 2010-02-15
Hi, oswaldkelso.  To answer your question, it's still got the original iMac keyboard.  Everything's up and running now, but it's VERY SLOW.  Surprising how much faster this machine runs with OS X Panther.

---

### Post by linuxopjemac on 2010-02-15
Maybe you need another window manager like [fluxbox]("http://www.fluxbox.org/") or something of that sort.

Have a look at [this article]("http://www.junauza.com/2008/08/20-most-nimble-and-simple-x-window.html").

---

### Post by oswaldkelso on 2010-02-15
Xubuntu can be a bit bloated. It's great for new users but on a machine of your spec. you really need to loose some baggage. I'd spend some time getting to understand the system first (slowly :P ) When your comfortable play with your system, but back up your data. 

Run the top command to see if your using all your ram.

Fire up a normal desktop with what you usually have running and see if your out of ram. 
```

top
```

even running blackbox, firefox, and rox-filer I'm on 97mb ram, most of that will be firefox and to many tabs. If you've only got 160mb you maybe pushing it.

[http://2.bp.blogspot.com/_7Y8k50qHvgs/Su9fo4jxRlI/AAAAAAAAAHI/jV4vDk8t2fM/s1600-h/imac-blackbox-rox.png](http://2.bp.blogspot.com/_7Y8k50qHvgs/Su9fo4jxRlI/AAAAAAAAAHI/jV4vDk8t2fM/s1600-h/imac-blackbox-rox.png)

---

### Post by LtPitt on 2010-02-16
Xubuntu is PURE bloatware!

Install a ubuntu server alternate and then install lxde.
(Fluxbox is damn fast but also "user-enemily" and ugly :P)
You'll have a revitalized imac! :)

---

### Post by StivVid on 2010-02-16
Just a quick question for linuxopjemac...  In the section above for configured video device, shouldn't I be using the ati driver instead of fbdev?  How would I make the change in the code to correct that?

---

### Post by linuxopjemac on 2010-02-17
Well, I am not sure whether you are going to be successful in that. I think many people tried that with a 166 MHz iMac. The config file I gave you is a working one, which was produced by trial and error.

You could try to change to the ati driver. Now you have this:

```
Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:18:0"
Option "UseFBDev" "true"
EndSection
```

You could change it into this:
```

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:18:0"
Driver "ati"
Option "UseFBDev" "true"
EndSection
```

Maybe you need to comment out the BusID section

```
#BusID "PCI:0:18:0"
```

You can try this:
```
Option "UseFBDev" "false"
```

You could also try a 
```
BusID "PCI:0:16:0"
```

---


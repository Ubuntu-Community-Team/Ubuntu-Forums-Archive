---
title: "Refreshing??"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-03-07
Hello to everyone,

Got Ubuntu amd64 version up and runnining, in a roundabout way, but the refresh on the monitor is set at 61 Hz.  The flicker is terrible and there are no option available to increase it.

I'm running a home-built setup... AMD Athlon 64, Asus A8N-E motherboard, Radeon X550 PCIE graphics card (256 Mb) and 1 Gb of RAM.  I was unable to properly configure my graphics card so tried a get-round I found on here...
'sudo dpkg-reconfigure xserver-xorg'.  Unfortunately I got a little confused with all the options it was throwing at me so I pretty much agreed to everything.

Anyway, I made it into the desktop and was also informed that there is a broken package file.  Help!!  :confused: 

Thank you in advance for all your helpful hints.

---

### Post by LordBug on 2006-03-07
Look up the horizontal and vertical refresh numbers for your monitor.  Edit xorg.conf, and add this information to the Monitor section.  I don't remember the option names 100% offhand, but it'll follow like this:

VertSync      "X-Y"
HorizRefresh  "A-B"

Should take care of the problem.

---

### Post by taurus on 2006-03-07
And just in case you don't know where xorg.conf is, it's in /etc/X11.  So, use a text editor to change the values for your monitor:  gedit (GUI) or nano (terminal).
```

sudo gedit /etc/X11/xorg.conf

```

---


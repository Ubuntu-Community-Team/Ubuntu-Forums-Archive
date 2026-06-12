---
title: "Xserver fails to start"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by niglch on 2007-03-17
I downloaded the Ubuntu 6.10 install / liveCD iso file, burned it to a CD, checked the md5hash (it was good), and rebooted with the disk in the drive. Everything seemed to go alright until I got a message saying "Failed to start the X-server (your graphical interface) ...". I half expected this because the same thing happened to me when I tried the openSuSE liveDVD. I was able to fix the issue, after browsing the SuSE forums for a similar problem, by logging is as root at the command prompt directly after getting the error and typing the following: ```
sax2 -p
sax2 -c1
startx
``` And to my surprise, x-server started up and I was able to get to the desktop.
Apparently, the issue was caused because I had both an Intel integrated graphics chipset and a GeForce FX 5200 graphics card (which was purchased and installed separately) in my computer.
I was hoping that I could follow a similar procedure for Ubuntu, but after I get the Xserver failure message, I can't figure out how to type any further commands. It spits me out at the black screen again with a flashing "_" symbol, but no "linux loggin:" prompt or something where I can login as root and enter further commands. It stays basically frozen in this state until I hit alt+ctrl+del to reboot. Does anyone know how to work around this issue?

---

### Post by AtrejuT on 2007-03-17
what happens if you press Ctrl+Alt+F1? That should normally get you to a console.
I doubt these sax-commands work in ubuntu, though-

atreju

---

### Post by fjf314 on 2007-03-17
After you use Ctrl + Alt + F1 to get to the terminal like AtrejuT said, you can use the following command to reconfigure X.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jbayone on 2007-03-17
You may want to try disabling the integrated graphics in your BIOS, then try Ubuntu.

---

### Post by Kobalt on 2007-03-17
I do believe sax commands are specific to Suse... 
I'd say you should follow jbayone's advise, or maybe someone more experienced in Ubuntu will give you the command to type at boot to avoid conflicting graphic cards.

---

### Post by pi3832 on 2007-03-17
> **fjf314 said:**
> After you use Ctrl + Alt + F1 to get to the terminal like AtrejuT said, you can use the following command to reconfigure X.

```
sudo dpkg-reconfigure xserver-xorg
```

(It's been over a decade since I've used any flavor of Unix so forgive me if this is a truly dumb question.)

Will that code work with any hardware or just the one the original poster is using?

I'm trying to get Dapper to load on an old iMac G3 (slot-loading) and I get the same error: X server failed.

Though, I do get a command-line prompt.  Can I use the code above to get the install going again?

Or is there a command-line install I can run?

---

### Post by niglch on 2007-03-18
Problem solved: After following you're instructions and figuring what the location of my video card was, I was able to get xserver to start.
My best guess is that xserver was auto detecting the integrated graphics chipset instead of the GeForce card. Anyway, after manually instructing xserver to use the "nv" driver, typing in the card name "NVidia GeForce FX 5200", and manually entering the PCI slot "02:09:0", xserver successfully started. In fact, I'm typing from the liveCD right now.
I must say, I'm very impressed. Everything works now, it amazing! All of my usb devices are detected, my sound works great, the video is good, and OMG I can print! Basically none of that stuff worked when I tried Fedora Core a while back and ended up just giving up. Thanks a lot, I think I'm going to install on my HD soon.

EDIT: For whoever else might be having this problem and in a similar situation, **make sure that you say NO to to using the kernel framebuffer device interface because it does cause problems in this case.** When I tried enabling it, xserver would not start.

---

### Post by shiningpathb4me on 2007-03-18
Uhh . . . which instructions did you follow to make it work? I have the exact same symptoms and ctrl-alt-f1 just gives me a flashing cursor too. I don't have onboard video though, I have only one video card, an ATI Radeon. And where did you find your PCI address for that card?

---

### Post by DustRatt on 2007-03-19
im having the same problem, help would be greatly appreciated. at the end of the error report it says that it can't find my video card(ati Radeon X850XT) 

"[I](WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
 (WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected![/I]"

idk why it has an older graphics chip-set there... that im not using...

help would be great...

---


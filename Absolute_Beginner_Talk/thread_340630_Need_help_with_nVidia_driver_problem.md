---
title: "Need help with nVidia driver problem"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by edwardLS on 2007-01-17
Some Background:  I have installed Ubuntu (Dapper Drake) on a dual-boot system at work, and at home.  These two systems are quite different; however, they both have nVidia graphic cards.  The two nVidia cards are different models, but both suffer the same problem when using the "nv" driver.  The problem is that the screen display is shifted to the right approximately a half inch.

Work Solution:  I installed (Synaptic) the nvidia-glx driver package and edited the /etc/X11/xorg.conf to replace "nv" with "nvidia".  I rebooted the system to Ubuntu, and I was able to see the "nVidia" splash screen, and the problem was solved. The graphics card is a GeForce2 MX/MX 400 installed in the AGP slot.

Home Problem:  I followed the same procedure with the nvidia-glx driver package and edited the /etc/X11/xorg.conf.  When I rebooted the system, I did not see the 'nVidia" splash screen, and the problem was not resolved. The graphics card is a PNY GeForce 6200 installed in the AGP slot.

My need of help:  Is not seeing the splash screen an indication that the nvidia driver is not installed?  Or, is it an indication that I need a different 

Any pointers or precise detailed help would be appreciated.

---

### Post by taurus on 2007-01-17
Did you remember to run

```
sudo nvidia-xconfig
```

Also, make sure you use "nvidia" instead of "nv" in /etc/X11/xorg.conf.

---

### Post by edwardLS on 2007-01-17
I double checked the /etc/X11/xorg.conf and it contains "nvidia".  I also ran sudo nvidia-xconfig.\, and in fact on the home system, that is what replaced the "nv" with "nvidia" in /etc/X11/xorg.conf.

---

### Post by taurus on 2007-01-17
Maybe you want to use this guide to install the latest version of nVidia driver then.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by edwardLS on 2007-01-18
I followed the instructions at [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html) for the use of "ENVY".  This downloaded and ran to completion with no errors that I was able to notice.  With a reboot I notice that I still do not get the nVidia splash screen.  I also noticed the following with respect to ?etc/X11/xorg.conf:
1. All instances of "nv" have been replaced with "nvidia".
2. The Device Name seems to be 'unknown'  

With respect to item 2, it seems that the PNY GeForce 6200 adapter is not being recognized/identified by the driver/installation.  I transcribed what was in that field, but unfortunately I forgot to bring the note with me to work.

The use of ENVY seems to have slightly improved the situation.  That is, my original complaint was the display was shifted about 1/2 inch to the right so that the ICON in the extreme right of both the top and bottom panels were not seen.  Since the use of ENVY the shift is now about 1/4 inch, and I am able to see approximately half of each of those ICONs.

Any further suggestions would be appreciated.

---

### Post by edwardLS on 2007-01-18
I believe that I have a solution to my problem.  Using 'nvidia-settings' I noticed that it knew that I had a GeForce 6200 GPU even though /etc/X11/xorg.conf did not.  Playing around with something I knew nothing about, I came across the "X Server Display Configuration" in the left side of the NVIDIA X Server Settings screen, and further noticed the "Save to X Configuration File" button.  I was at this point about ready to re-install and start over again with ubuntu (Dapper Drake) so - why not?  A look at the /etc/X11/xorg.conf now indicates that it knows that I have a GeForce 6200 GPU.  I re-booted, seen the nVidia splash screen, and the display is perfectly positioned on the screen.

---


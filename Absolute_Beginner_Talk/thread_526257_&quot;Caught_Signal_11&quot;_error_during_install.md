---
title: "&quot;Caught Signal 11&quot; error during install"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by kklingerman on 2007-08-15
Hi, 

  I amtrying to install Feisty natively (as opposed to in a vmware slice) on my Dell Inspiron 1505 laptop.  When I select install, I get a blank screen.  When I change the display to another resolution, I get a screen until it errors outr with:  "Caught Signal 11.  Server Aborting".  

  I suspect it is a video driver issue.  I have a ATI Mobility Radeon 1400.  I am pretty new to Linux, so any assistance would be appreciated.  Thanks.

---

### Post by 1/0 on 2007-08-15
I've never had an ATI card but my guess is that your xorg.conf has some errors. You can see in /var/log/Xorg.0.log or /var/log/Xorg.0.log.old as well as in /etx/X11/xorg.conf.

My guess is that in Section "Device" the Driver will be wrong. You could just do:

```
sudo dpkg-reconfigure xserver-xorg
```

and then manually check that the driver is ati or whatever it is supposed to be.

---

### Post by kklingerman on 2007-08-15
How would I do that when I am booting off the CDROM to get the installation to run?  Maybe I wasn't clear, but I am not even getting to the installation to HD yet.  Any ideas?  Thanks.

---

### Post by 1/0 on 2007-08-15
Doh! Not installed yet. Have you tried the altarnative install cd? Its usually better on graphic card issues.

---

### Post by kklingerman on 2007-08-15
Got it!  Found another post withthe solution (I did search before posting).  

I set the resolution to 640x480 before install
Viewed the debug info to get to the command line

From the command line:

sudo dpkg-reconfigure xserver-xorg
pick all defaults and make sure VESA is selected
remove all video resolutions except 640x480
HorizSync = 36-52
VertiRefresh = 36-60
Save settings
type 'startx'

System is installing now.  Hope I don't further video issue.  I'm overwriting my Micro$oft partition. :guitar:

---


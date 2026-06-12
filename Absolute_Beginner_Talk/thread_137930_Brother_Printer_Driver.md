---
title: "Brother Printer Driver"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by rogowar on 2006-02-28
I posted this once in the hardware section ( [http://www.ubuntuforums.org/showthread.php?p=747503#post747503](http://www.ubuntuforums.org/showthread.php?p=747503#post747503) ), but it may have been too basic, so I'll try again here.

I'd like to install a more fully featured printer driver for my Brother MFC-8840DN, hoping to be able to take advantage of duplexing and the rest. I did find that they have Debian binaries ready to roll (both a driver and a CUPS wrapper), so I'm feeling all snazzy about accidentally choosing a printer with linux support.

I fiddled about a bit, with no luck, until I found this fairly handy guide for installing brother drivers on 5.04 here:

[http://ubuntuforums.org/showthread.php?t=26426&](http://ubuntuforums.org/showthread.php?t=26426&)

However, one of the required packages, libqt3c102, is no longer available for Breezy (or so I gather). I found someone complaining about a .deb for Skype saying that libqt3c should work if you can edit the "Depends: line of the control file" which puts me in the tall weeds. Brother does supply the source, so conceivably you could presumably alter the dependencies, but that goes beyond my comfort level.  

Anyone who actually knows what they're doing got any advice? Many thanks!

---

### Post by Pragmatist on 2006-03-01
Have you looked in synaptic: ```
sudo synaptic
```
I just did a search for libqt3c102 and found a package (available, but not installed by default) called: libqt3c102-mt

---

### Post by rogowar on 2006-03-03
[QUOTE=Pragmatist] just did a search for libqt3c102 and found a package [/QUOTE]

Well I seem to have gotten beyond the libqt3c102 issue by installing the libqt3c compatibility headers (maybe), but now my issue seems to be different.  I *seem* to have the drivers installed, and I can certainly print, but the duplexing option doesn't work.  I can see in the printer properties the options DuplexNoTumble or DuplexTumble, but it has no effect on the output.  

Ideas?

---

### Post by Pragmatist on 2006-03-03
You might want to check out PPD configuration files:

[http://www.linuxprinting.org/basic-printing-faq.html](http://www.linuxprinting.org/basic-printing-faq.html)

and ```
man -k ppd
```

---


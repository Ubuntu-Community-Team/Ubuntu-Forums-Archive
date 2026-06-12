---
title: "Canon MP450 + Virtualbox?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by onero on 2007-09-10
Hi everyone,

My mother went and bought a printer without consulting me (eep), and she got a Canon MP450 multifunctional (printer, copier, scanner). I checked the Open Printing DB, and it seems that the only Linux drivers available for it are from Turboprint, and they cost about half of what the printer cost >.<

Anyway, I managed to set it up as a USB device in Virtualbox and installed the drivers in the Windows guest. I can print from my Windows guest (yay), but for the life of me I cannot get the scanning to work. I always get a communication error of some sort. Does anyone have any idea how to fix this? Or at least what's wrong?

Alternatively, if you know of any other way I can get the printer/scanner/everything working under Ubuntu (that doesn't involve virtualization), that would be great. Thanks!

---

### Post by rsk02 on 2008-03-20
This may come rather late but I thought I would post my findings anyway. I have the same multifunction device you refer to. I was able to get it working (at least under Gutsy).

Printing:

I just plugged in the device and went to System ->Administration-> Printing. The device was detected as Canon MP 450. I clicked on the "Change" button for "Make and Model" and chose "Canon" -> MP150-> CUPS+Gutenprint v5.0.1. You get the same results for MP500 also.

Scanning:

Install Sane + Sane-Utils (Go to Synaptic or use apt-get). You may want to install XSane also. To verify, go to Terminal and type sane-detect and your device should be detected as Canon Pixma MP450. You can try scanimage -L to confirm.

Just fire up Xsane and it should see your scanner right away. I was able to scan. Don't dink with the "experimental" button support.

I had the same problem in Virtualbox. While I haven't, you may want to try disabling EHCI support under the USB settings for your VM. This seems to be the cure-all touted for all Virtualbox USB woes.


Hope this helps.

---

### Post by nefrin on 2008-05-08
Updates:

Canon PIXMA MP150 - CUPS+Gutenprint v5.0.2  This seemed to be the only working printer driver for me, and I am using Ubuntu 8.04 with all the latest updates. At least it prints from Linux.

The Sane + Sane-utils also worked for the scanner on 8.04 (the xsane was already installed on my system).

I have been looking for a way to get this to work for days, you are a life saver rsk02

---

### Post by gib2800 on 2008-06-17
Thanks Rsk02. I was having the same problem with Kubuntu 8.04.  I could not change the make and model from within Kubuntu's system settings panel, but had to instead open a web browser and type in:
[http://localhost:631/](http://localhost:631/) 
which brought up the CUPS configurations.  From there I added the printer and had to set it up as: Canon Pixma MP150 CUPS+Gutenprint v5.0.2 en.  It would not work as the MP500 for me.

---


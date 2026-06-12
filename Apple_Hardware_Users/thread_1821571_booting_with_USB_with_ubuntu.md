---
title: "booting with USB with ubuntu"
date: 2011-08-09
forum: Apple Hardware Users
---

### Post by haiiyaa on 2011-08-09
I want to start playing around with ubuntu and for the moment without messing around with partitioning my mac and doing a dual boot. So, I installed ubuntu on my USB drive as per the instructions on the download page to create a usb stick for mac. 

After following the instructions when I restart the mac with alt key pressed, I don't see the option to boot from the USB key. I just see the option to boot from the Mac HD or Recovery. 

I have OS X lion, installed and a MacBook Intel Core 2 Duo machine. 

Any suggestions? Thanks

---

### Post by rubbersoul.josh on 2011-08-09
i don't think the mac will support booting from usb without refit installed.

install refit and then try booting from usb.

---

### Post by jonny on 2011-08-09
Macs work slightly differently from PCs, and the standard tool for making a bootable USB drive is configured for use with PCs.  Try following the instructions [here]("http://ubuntuforums.org/showpost.php?p=11093491&postcount=43") to put Ubuntu on your USB stick - although this method does, unfortunately, make the slightly circular presupposition that you already have access to a working ubuntu installation.

---

### Post by haiiyaa on 2011-08-09
Thanks, I'll give this a try. I don't already have an ubuntu or any linux installation, so i might have to create a virtual image using virtualbox and then make the USB. Will update the thread once i have tried this.

---

### Post by jonny on 2011-08-09
> **haiiyaa said:**
> Thanks, I'll give this a try. I don't already have an ubuntu or any linux installation, so i might have to create a virtual image using virtualbox and then make the USB. Will update the thread once i have tried this.
If you have a Windows PC and a spare memory stick, you could boot the PC into Ubuntu with the USB stick that you've already created and work from there.

---

### Post by haiiyaa on 2011-08-10
I made some progress, but not there yet. After following the instructions here, [http://ubuntuforums.org/showpost.php?p=11093491&postcount=43](http://ubuntuforums.org/showpost.php?p=11093491&postcount=43) . In addition to this, i also needed to install refit. Now during start up i get the refit screen with the option to choose linux as well. 

The problem is when I select linux i get a screen with  'No bootable device. Insert boot disk and press any key' message. 

I saw this post [http://ubuntuforums.org/showthread.php?t=829476](http://ubuntuforums.org/showthread.php?t=829476). But that talks about when installing ubuntu on the hard disk itself. I am not sure if this would work for my situation. 

any other clues?

---


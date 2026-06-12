---
title: "Need Help Installing (K)Ubuntu 6.10 to USB2 Drive"
date: 2007-04-01
forum: Apple Intel Users
---

### Post by koni2005 on 2007-04-01
Hi there,

this topic has probably been discussed over and over. But I still haven't found a way to make it work.

My Configuration: MacBook Pro 2.16 Core Duo, 100 GB HD, 2GB RAM.
I have OSX and XP installed on my internal HD. The HD is pretty full, so I would like to install and boot Ubuntu on / from an external USB2 HD. Refit works and also recognizes the USB Drive.

Fearing I might erase my internal HD - or damage the mbr - how should the partition table for the external Drive look like? Do I need GRUB, or does Refit do the trick already? Any suggestions? Or a link to someone how has managed to install and boot Ubuntu on an USB Drive???

Thanks!

---

### Post by siepo on 2007-04-01
I couldn't get it to work either. Installation wasn't the problem, but I couldn't boot the external installation, neither from a grub on the internal drive, nor from a grub on the external drive. Grub just doesn't seem to see the external drive, although rEFIt has no problems. I also tried firewire, with the same luck.

---

### Post by koni2005 on 2007-04-01
Well, funnily after a couple of tries I managed to get a version running - I used the graphical install from the Live CD. And it worked. I was able to boot from the USB drive - refit recognized everything correctly. But there were some really weird problems with the xserver and the whole system as a whole. For example I could never set the display to my native resolution of 1440x900 etc. After updating the kernal with apt-get the installation was wracked completely and would just crash at various points during booting...

I'll give it a try with 7.04 beta, lets see...

---

### Post by zaqarov on 2007-12-08
Any progress?

Sorry for bringing this topic back, but I know this would help a lot of people.

zaqarov

---

### Post by cyberdork33 on 2007-12-09
This is the best information available:
[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

---


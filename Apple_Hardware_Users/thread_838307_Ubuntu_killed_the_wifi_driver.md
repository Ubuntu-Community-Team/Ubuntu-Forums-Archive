---
title: "Ubuntu killed the wifi driver?"
date: 2008-06-23
forum: Apple Hardware Users
---

### Post by dellegazze on 2008-06-23
Okay, so, everything was working just fine on my ubuntu (hardy) macbook (santa rosa) installation. Then, going about my usual business, i booted up, and it didn't show any wifi networks. "No problem," i thought to myself, and checked the router and the cable modem. Then, when everything was fine with those, I attempted to plug in directly via ethernet and use [these]("https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688") directions, which i had used to originally get the wifi drivers up and running. Still no dice.

So, I beseech you, fair and noble Ubuntu forum members, to attempt to solve my problem.

---

### Post by TheCage on 2008-06-23
Hi Dellegazze, I also use Ubuntu on a Macbook pro and I have found the wifi to be 'sketchy' at times myself. Firstly, the drivers need to be re-compiled after each kernel upgrade (understandable), but sometimes for no reason when I boot I find the driver appears to not work.
What I do is go to SYSTEM > ADMINISTRATION > HARDWARE DRIVERS and then disable and then re-enable the driver. After reboot it appears fine. Not a fix I know, but some help I hope!

---

### Post by dellegazze on 2008-06-23
Still no luck. :\

I opened the Hardware Drivers screen, and nothing was there. When I saw this, I tried to reinstall the driver, restarted, and checked again, and still nothing.

---

### Post by cyberdork33 on 2008-06-23
> **dellegazze said:**
> Still no luck. :\

I opened the Hardware Drivers screen, and nothing was there. When I saw this, I tried to reinstall the driver, restarted, and checked again, and still nothing.
unfortunately that would not work if you had to compile the drivers. You will need to recompile. Follow the directions in the wiki again.

---

### Post by dellegazze on 2008-06-23
> **cyberdork33 said:**
> unfortunately that would not work if you had to compile the drivers. You will need to recompile. Follow the directions in the wiki again.

That's what I just did. Hence "When I saw this, I tried to reinstall the driver, restarted, and checked again, and still nothing".

Any other advice?

---

### Post by cyberdork33 on 2008-06-24
> **dellegazze said:**
> That's what I just did. Hence "When I saw this, I tried to reinstall the driver, restarted, and checked again, and still nothing".

Any other advice?

"still nothing" doesn't help diagnose the issue. Give more information. How do you know if the module is loaded? If loaded, does the system see the device? What does "it doesn't work" what do you do to see it doesn't work.

---

### Post by dellegazze on 2008-06-24
well, the network manager applet isn't recognizing any wireless networks, System > Administration > Hardware drivers isn't recognizing any drivers, and following the macbook guide on the wiki isn't doing anything.

---

### Post by dustynus on 2008-06-25
This has worked for me on my macbook 2,1 duo core, it is santa rosa
Try doing this, you'll get an internet connection, so grab the ethernet for a couple minutes. I've upload a revision of madwifi that I use constantly.
I've installed it multiple times on amd64 and the 32 bit hardy. give it a try, it should work.
I've uploaded the madwifi drivers here:

[http://rapidshare.com/files/124992436/madwifi-trunk-current.tar.gz.html](http://rapidshare.com/files/124992436/madwifi-trunk-current.tar.gz.html)
Download that, and then untar it onto your desktop.

```

cd ~/Desktop
sudo modprobe -r ath_pci
sudo apt-get install build-essential
cd madwifi[tab]
sudo make
sudo make install

```
This is going to get the essential stuff to build madwifi, so you shouldn't get any errors. 
If you don't get any errors from make and make install, then follow up and do this:
```
sudo modprobe ath_pci
```

Click on your gnome desktop network thing, and you should see ''wireless''
Give it a minute and it'll load up the networks visible.

Oh and if it cuts out, or something, just try reloading ath_pci, that seems to always fix problems for me.

---

### Post by dellegazze on 2008-06-27
Sorry for the long time between replies - I completely lost this thread and had to sift through the Apple Users Forum. I bet there's a better way to find my threads but I couldn't find it...

Okay, so I tried plugging in to the ethernet. The network applet recognizes that there's a conncection, but the connection to the internet isn't being recognized. I opened firefox, pidgin, etc., and they all said no connection.

---


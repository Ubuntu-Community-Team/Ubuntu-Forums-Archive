---
title: "Help with Linux wlan ng"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by thespursfan on 2006-04-08
I am currently connected to the internet with an ethernet cable to my wireles router. I want to use my wusb11 2.5 adapter to connect to the internet though.
I downloaded the linux drivers for this particular adapter and go to install the driver.
 After reading the README, and doing what it says this is what I get:

> 
-------------- Linux WLAN Configuration Script -------------

The default responses are correct for most users.

Build Prism2.x PCMCIA Card Services (_cs) driver? (y/n) [y]: y

Build Prism2 PLX9052 based PCI (_plx) adapter driver? (y/n) [n]: n

Build Prism2.5 native PCI (_pci) driver? (y/n) [n]: n

Build Prism2.5 USB (_usb) driver? (y/n) [n]: y

Linux source directory [/usr/src/linux]:
Linux source tree /usr/src/linux is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed

make: *** [config] Error 1


I am on Kubuntu, and just installed it recently. I am very new to linux and don't understand how to get around this error. Is there a directory on my system that has the "Linux source tree"?? Any ideas on how to get past this? Thanks for any help you can provide.
I've been messing around with this for hours, and I need to sleep ](*,)

---

### Post by trent dillman on 2006-04-08
sudo apt-get install build-essential linux-source

---

### Post by thespursfan on 2006-04-09
Thanks for replying Trent.
I entered that and this was the output:
> Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
Package linux-source is a virtual package provided by:
  linux-source-2.6.12 2.6.12-10.30
You should explicitly select one to install.
E: Package linux-source has no installation candidate

Any thoughts as to what that means?

---

### Post by trent dillman on 2006-04-09
Snap. You're on Breezy (I'm using Dapper...I need to watch myself!). Go to Synaptic, and search for linux-source. Find the one that goes with your kernel.

To get your kernel version, open the terminal and use:

```
uname -r
```

---

### Post by thespursfan on 2006-04-09
Oh, ok. I have used Adept. Is that the same thing as Synaptic more or less?
If so, I have installed 2.6.12. Not really sure what to do next though.
Is there a directory that the source is in, that I just don't know about?

---

### Post by thespursfan on 2006-04-09
Still looking for some help with this. Any ideas?

---


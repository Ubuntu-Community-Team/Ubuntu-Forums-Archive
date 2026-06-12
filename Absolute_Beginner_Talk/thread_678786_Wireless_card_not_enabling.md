---
title: "Wireless card not enabling"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-26
Hi this is Fraser's brother, who tried to use Ubuntu from a live CD, which works fine, apart from the fact that it cannot connect to our wireless network, apparently it lacks a driver called "bcm43xx-fwcutter". Where would I get such a driver?

The computer is a Dell Inspiron 1501 laptop.

---

### Post by Fraser from Scotland on 2008-01-26
I've been looking at various bits and bobs, and the wireless card is a Broadcom BCM94311MCG wlan mini-PCI. I looked at something called "ndiswrapper", but I have no idea what to do with it!

---

### Post by theproc64 on 2008-01-26
If you are connected through LAN you can go to System>Administration>Restricted drivers manager and then check the box and download the driver.  Sometimes this driver doesn't work great though and after you install you should try using ndiswrapper.  I followed [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") and now my wireless is faster and has more range than with the restricted driver.

---

### Post by mikeyphi on 2008-01-26
> **Fraser from Scotland said:**
> Hi this is Fraser's brother, who tried to use Ubuntu from a live CD, which works fine, apart from the fact that it cannot connect to our wireless network, apparently it lacks a driver called "bcm43xx-fwcutter". Where would I get such a driver?

The computer is a Dell Inspiron 1501 laptop.

The 'driver' you quote is not actually a driver, it's a tool for (hopefully) installing the driver -  however, it is available through Synaptic.
Give it a try

If that doesn't work - try to find the exact model of your card
then look here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

---

### Post by mikeyphi on 2008-01-26
Post #3 gave a nice guide....I see you're on gutsy so look here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by jan quark on 2008-01-26
try this tutorial I have wrote some time ago
and now I am online :)
[http://janquark.fatfreehost.com/tutorial1.html](http://janquark.fatfreehost.com/tutorial1.html)

I have the same wireless card

---


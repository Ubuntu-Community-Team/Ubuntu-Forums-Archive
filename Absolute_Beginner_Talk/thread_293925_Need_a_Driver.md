---
title: "Need a Driver"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by moonman4au on 2006-11-05
I am in desperate need of a driver for my wireless usb adapter.  I am trying to connect to my wireless network with a Belkin usb stick.  The model number is F5D7050.  It is a "g" adapter. I contacted Belkin and they do not currently publish any drivers for linux.  Any help would be appreciated.  I will not be able to leave linux on this machine if I am unable to connect to the internet.

Thanks

---

### Post by dmizer on 2006-11-05
with any wireless card, i always start here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) when trying to figure out if it will work or not.  your adapter is not listed, so it may be difficult for you to get it working.  usb adapters seem to be particularly troublesome.

that doesn't mean your card can't work.  you might take a look here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) it's usually quite helpful.

also you might have success with ndiswrapper, but i'd suggest exausting other resources first, as ndiswrapper can be a pain to configure correctly.

---

### Post by FrodoB on 2006-11-08
There are at least 4 versions of the F5D7050 in existence, which one do you have?

---

### Post by Blutack on 2006-11-08
Ndiswrapper a pain?  sudo apt-get install ndisgtk.  Nice graphical utility for installing ndis drivers.  I use ndiswrapper cos its easier than natives (I know its the wrong atitude to take).

---

### Post by FrodoB on 2006-11-09
The problem with ndiswrapper is that it is very situation dependent. I have seen situations where it worked fine on one particular kernel, in one particular Linux OS, with a particular ndiswrapper and Windows driver and no others. 

In my experience ndiswrapper cannot be treated like a surefire solution to everyone's wireless device issues. 

I use it successfully in about 25% of the cases where it could be  applied. I have also seen cases where upgrading to the latest version of ndiswrapper makes the situation worse or caused the setup to fail.

If it works well in a particular case, then it should be posted with exact situation details for others to use, but don't be surprised if it fails as soon as something gets upgraded.

If you can get native drivers to compile and install they are usually much more stable. But sometimes they stop compiling on new kernels as well.

I can understand dmizer's pain on the issue.

---

### Post by FrodoB on 2006-11-09
moomman4au;

There are certainly good native drivers out there for at least two versions of the F5D7050, the ver 3000 and ver 4000 devices are in use here.

Can you tell which one you have and it you do not have the box then publish the output from lsusb and we should be able to determine which one it is.

FrodoB

---


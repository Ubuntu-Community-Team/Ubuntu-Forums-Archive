---
title: "Wireless driver"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Runestave on 2006-11-11
I was just going around the net collecting up to date drivers for all my hardware in prep for wiping and reinstalling Winblows (yuk) because I'm not yet ready to make the switch.

One of the things holding me back was the apparent difficulty in getting wireless network cards to work in Linux distros.

But there on the [www.smc.com](www.smc.com) page (SMC Networks, the mfgr of my card), among the driver downloads for my specific card, are some Linux choices!

But which one do I want? I have no idea how their version numbers correspond to Ubuntu. They list drivers for Unix, Linux 2.2.x, Linux 2.4.x and Linux 2.6.x.

Any idea which I should try?

---

### Post by qscgz on 2006-11-11
[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless)

[https://wiki.ubuntu.com/FindPage](https://wiki.ubuntu.com/FindPage) "Title Search"

check this, please.

---

### Post by Runestave on 2006-11-15
Okay. I've researched the card and chipset, and gone to the ndiswrapper wiki and found it. It says:

***
Card: SMC 2802W V2 
Chipset: [Intersil Corporation] Intersil ISL3890 Prism GT/Prism Duette? (rev 01) 
pciid: 1260:3890 (rev 01) 
Driver: SMC Europe [http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip](http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip) 
Other: Gentoo 2.6.7, Ndiswrapper 0.9+CVS@040812 Manual compile (not ebuild); removed 0.8 that came from portage; worked for me after I reinstalled the driver with newly compiled version 
***

I have downloaded the linked drivers file. Now what do I do with it? Do I also need ndiswrapper? Where do I get that, and what do I do with *it* when I get it?

---

### Post by nickpaton on 2006-11-15
Unzip the file you have downloaded into, say your Home folder.
The file you are interested in is the 2802W.inf file under Driver>WinXP.

The easiest way would be to use Ndiswrapper's GUI which can be got from 
[www.automatix2](www.automatix2).

I believe all the packages you need if you are not using automatix are:

ndisgtk
ndiswrapper-utils
ndiswrapper-source

Having installed automatix, install Ndiswrapper and Network Manager.

You will now see a new folder under Administration>Windows Wireless Drivers.

Click on "install new Driver" and navigate to where 2802W.inf file is kept.

You should now see in the main box, "Hardware Present: yes", meaning that the software has found the hardware.

Go into "Configure Network" and tick the wireless connection and remove any tick against the wired connection.

Don't at this stage go into properties and configure any encryption, but you will need to add the SSID if you have already specified one on your modem router.  (Temporarily disable any encryption in your router as well)

What you now need to do is get the default device to become the same as the wireless device, and in Dapper I've always struggled to get this to happen.  But it then suddenly seems to connect.  Play around with also enabling the wired connection, and I seem to remember that it requires reboots etc.

Once you have a wireless connection, set up for WEP incryption.  Note your password type is Hexidecimal.

Hope this helps.  Can other's please check this over, since I use a broadcom driver and not familiar with this type.

---


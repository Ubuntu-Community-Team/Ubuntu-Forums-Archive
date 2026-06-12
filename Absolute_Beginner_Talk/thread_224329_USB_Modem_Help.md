---
title: "USB Modem Help?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Steve1492 on 2006-07-27
Well I just got Xubuntu today,and i got everything working ok.But i cant seem to figure out how to get my USB modem set up.

Xubuntu is detecting it (the USB light on the modem is lit) but when i opened Firefox it sais the server could not be found.

How do i configure my USB Modem for Xubuntu?:confused: 

Oh and hello all im new here!The site looks prety nice,im glad to join!

---

### Post by coffeecat on 2006-07-28
Since you don't say which make and model of USB modem you are using, it's a little bit ( :wink: ) difficult for anyone to advise you how to set it up. Having said that, a few general points:

USB modems are mostly (always?) designed for Windows and do not even work in Windows without installing drivers. You can get USB modems to work in Linux, but it involves a lot of editing of system files, etc. A bit daunting for newcomers.

The fact that the light is coming on may only mean that the modem is getting power from the usb interface, not that Xubuntu has detected it.

USB is not designed for networking. USB modems are second best options. Assuming that you are using adsl (you don't say), it would be far better to get yourself an ethernet modem/router. You won't need to install a driver because the device will be independent of whatever OS you use on your computer.

But if you really want to give yourself a hard time, post the details of your USB device and someone might be able to point you to a howto for it. Rather you than me! :) And if you are not using adsl, give us details of your internet connection as well.

And lastly - hello to you too. I hope you enjoy Linux in general and *buntu in particular.

---

### Post by Steve1492 on 2006-07-29
Sorry for being so inspecific...

My modem is a Westell Wirespeed 6100.

But the thing is,the modem has a USB port and an Ethernet port,and my PC doesnt have an ethernet card,so I use the USB for my internet connection.

I'd appreciate any help :biggrin:

---

### Post by Neobuntu on 2008-03-29
Hmmm, I wonder if one could use ndiswrapper with the actuall USB **Win XP** driver and get that to work? ...just a thought.

Anyone do that?

**Edit:** Oh yeah! Do a > lsusb and see how it is listed. Then, search that text on Google for others that may have done it with Ubuntu "ubuntu forums". 

Of course, the easist thing to do is bum a ethernet card (NIC). Aproximate value, $5 or less (100BT type PCI card for desktops or PCMCIA card for notebooks). Just ask around. Trust me, a quick hardware solution beats software setup (on anything, Windows being harder now-a-days)  ANY DAY! Any time you can avoid driver setup, you save time. lots of it. It's easiest to do with *ubuntu. (I use kubuntu and love it. Think of it as the least of all OS "evils"; on most things.) the devil is truly in the details.

The best thing about *ubuntu, are the details reduced! ...For the power hacker and newbie alike.

---


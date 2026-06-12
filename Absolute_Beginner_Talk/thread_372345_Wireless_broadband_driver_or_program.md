---
title: "Wireless broadband driver or program???"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-02-28
Hi previously I wasnt able to get broadband but now I've just purchased wirless broadband and it came with a modem that plugs into the usb port of your desktop and a installation cd that you guessed it only supports windows. Would anyone be able to tell me if there would be a program I could download that could interface with my new purchase on Linux and allow for my internet????

---

### Post by Ek0nomik on 2007-02-28
What kind of modem is it?

Run a search for ndiswrapper.  That's how I got my Wireless card to work.  I got the Dell drivers from dell.com, and used ndiswrapper to make them work.

Hope that helps!

---

### Post by nite owl on 2007-02-28
It looks like its by a company called maxon. But it's hard to tell because the broadband company thats selling the wireless broadband has made it, it's own and put it's logo all over it. The company dosent have any linux drivers??? Would just installing this program 'ndiswrapper' work?.  What is it exactly?

---

### Post by Ek0nomik on 2007-02-28
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

"Some vendors do not release specifications of the hardware or provide a Linux driver for their wireless network cards. This project implements Windows kernel API and NDIS (Network Driver Interface Specification) API within Linux kernel. A Windows driver for wireless network card is then linked to this implementation so that the driver runs natively, as though it is in Windows, without binary emulation."

"With ndiswrapper, most miniPCI (builtin), PCI, PCMCIA (Cardbus only) or USB wireless network card works in Linux with x86 or x86-64. Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., **USB to serial port device**, ethernet card, home phone network device etc."

Installing ndiswrapper is relatively easy.  Getting the driver to work may be another story...

---

### Post by Ek0nomik on 2007-02-28
I am pretty new to Linux.

However, for my wireless drivers to work, I had to install ndiswrapper, than install a .inf file that came from extracting my wireless drivers.  Whether or not is is that simple for *your* case I don't know I'm afraid.  :/

---

### Post by plbee on 2007-04-09
> **nite owl said:**
> Hi previously I wasnt able to get broadband but now I've just purchased wirless broadband and it came with a modem that plugs into the usb port of your desktop and a installation cd that you guessed it only supports windows. Would anyone be able to tell me if there would be a program I could download that could interface with my new purchase on Linux and allow for my internet????

Hi nite owl, I have the same modem and also trying to get it to go on Bigpond NextG. It's a Maxon BP3-EXT. Have you had any success with it yet? I've tried a few things, but had no luck at all. Pls advise if you got it working.
Tnx Plbee

---

### Post by rosco99 on 2007-06-14
Have you read the article -http://quozl.linux.org.au/bp3-usb/.
Several peole have got their Maxon working. I haven't got mine going yet but I think there is a bug in my USB connection.
If you get it working you might like to outline the steps here.

---

### Post by sharke on 2007-06-21
I have the same bigpond modem and have been lucky enough to get it working by following quozls instructions .
i have a post on instructions how to do this using sierra module which gives me double the download speeds of windows using bigpond supplied driver [http://ubuntuforums.org/showthread.php?t=477067](http://ubuntuforums.org/showthread.php?t=477067)

Regards
Sharke

---


---
title: "No Networking Lombard: Wireless, Cable, or Modem"
date: 2007-03-26
forum: Apple PPC Users
---

### Post by Blue DaNoob on 2007-03-26
Complete Linux Noob here.

I had a successful install of Ubuntu Edgy Eft 6.10 on my PowerBook PPC G3 Lombard last night, and I'm looking forward to getting some work done on my "New" laptop.

I installed Linux because I am having some problems (hardware, I think), that OSX can't seem to wrap itself around.  I am mentioning my problems here specifically, in case they are the cause of my inability to get any kind of networking established.  

The computer does not restart or boot-up normally without first pressing the reset button (PMU) on the back of the computer.  The computer will chime, but the screen will remain black, until PMU is pressed and power button is then pressed again.  I tried every Apple solution I could find, zapping PRAM, firmware, logging in as single user, cache clearing, reset-nvram, etc. etc., so  I'm thinking the problem is hardware.  I can't install OSX, because the OS is spread across 3 disks, and having to reset the PMU in order to reboot means the installation never can get past the first disk - it must lose it's place in the install process because I must be blanking out that section of memory when it tries to restart, or something.  Anyway, result is a circle with a line through it in place of the Apple logo on the start up screen.  I even tried partionning, and installing from OS 9.  I'm not sure if it's related, but in addition to this restart problem, the fairly new NewerTech battery I have no longer charges.  It shows as being plugged in (Linux and OS X) but won't charge up.  If I unplug the computer, it will last about a minute before just dying.  Even with Power management settings set to Shut Down on Linux.

So since I can't install OS X, I thought this would be a perfect time to jump into Linux.

The install was completely successful on the first try with a Live CD.  I wiped out the drive, so now there's nothing but Linux.  Everything works great except for Networking.  I can't get anything at all to work.

Wireless:  I have a MacSense AeroCard Plus 802.11b Wireless PCMCIA card.  The light is on, but there is no reference to it in the Networking tab.  Wired and Modem connections are there, but no wireless.  I have read that this card is RealTech chipset.  There are both Mac and Windows drivers, but I have also read that ndiswrapper does NOT work on PPC hardware.  Not that I really figured out ndiswrapper anyway.  I hoped that maybe running software update would magically discover this wireless card, so I tried to plug in the ethernet.

Ethernet:  Listed as wired connection, DHCP.  Plugged it in, and still no internet.  I looked at networking tools, and there *seemed* to be traffic, but FireFox and Update don't see the internet.  Everything looks similar to what my OS X G4 is set to for connecting, but no dice.  It's a PCX2200 Toshiba cable modem connected to Cox Cable.  I tried rebooting everything, still no joy.  In the networking window, the Wired connection is checked off, so I thought it looked good.  Figured I'd go with dial up.

Modem:  Another dead end.  in the networking tab, it had a dash through the box, so I added the basic info, phone number and password, and selected the default connection to the internet option.  I can't figure out how to get it to dial or even give me an error.  Opening Firefox simply gets me a page not found.  I cycled through all the connections, too /modem, /ttySo, etc...

So I'm stuck.  I know the wireless card was working in my previous install of OS X (I wiped it because I was going to ditch it - when I couldn't re-install OS X, I needed to look at other options).  I'm not so sure about the modem or the ethernet

Sorry for the long post, but I've read the more detail the better, so hopefully someone out there has battled with one of these problems before.  Of course my first choice would be getting the wireless working - I could care less about ether or modem if that works.  I'm new to both Linux and the command line.  I've read through the threads and can't seem to find the right answers.  Thanks in advance for any assistance!

---


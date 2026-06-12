---
title: "Can't connect to Internet"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by don skoog on 2007-02-02
Hi Guys,

I've been trying for two weeks to connect my newly installed Ubuntu 6.06.1 to the internet.

It's in a Thinkpad 600.
The Wireless card is a Linksys Wireless-G
I'm trying to connect to my Apple Airport Base Station

System>Administration>Networking lists: Wireless Connection and Modem Connection but does not show my wireless card by name. I have typed my setting in many times with no results.

So I'm assuming it doesn't recognize my card.

The computer is partitioned and the Windows system connects to my base station with no problem so I thought I try to use it as you guys outlined in [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

This creates new problems:

I can't check to see if it has a broadcom chipset because I don't know how to type in the upright line in <lspci | grep Broadcom\ Corporation> (I'm writing from my Mac and just copied the command here).

I can't install the bcm43xx-cutter (which sitting on my desktop) because<sudo apt-get install bcm43xx-fwcutter> returns with "no such file"

Synaptic Package Manager (after I searched and found bcm43xx-cutter) shows no package to install. Reload tells me "Could not download all Repository indexes and lists four repositories ([http://us.archive.ubuntu.com/ubuntu/....gpg:Temporary](http://us.archive.ubuntu.com/ubuntu/....gpg:Temporary) failure resolving 'us.archive.ubuntu.com', for example).

I'm stumped. Is there another approach or should I just buy a Linux supported wireless card? Can you recommend a wireless that will work without all this hassle?

Help!

Don

---

### Post by Paerez on 2007-02-02
open a terminal and run "lspci" and paste it here. You can open a terminal from Applications->Accessories->Terminal.

---

### Post by don skoog on 2007-02-02
Sorry, I can'y paste the results here. It's along result, the Thinkpad can't connect to the internet, and I can't transfer the info to this computer because my X11 isn't woking and I can't open Open Office on this computer. It's been that kind of day.

There is one result that might help, though:

Network Controller:Broadcom Corporation BCM4306 802.1 lb/g Wireless LAN Controller (rev 03)

Does that help?

Don

---

### Post by Paerez on 2007-02-02
yeah that is a tough card to get working. You have to use ndiswrapper. There are a bunch of howtos on the forums.

In the mean time, use a cable to get online.

---

### Post by don skoog on 2007-02-02
I give up. Three weeks to get Ubuntu running. Two weeks to connect to the internet, and counting.

Can you recommend a wireless card that would work easily and with a minimum of hassle?

---

### Post by Paerez on 2007-02-03
The only ones I have experience with are the Intel ones that come built in to laptops nowadays. Sorry.

---


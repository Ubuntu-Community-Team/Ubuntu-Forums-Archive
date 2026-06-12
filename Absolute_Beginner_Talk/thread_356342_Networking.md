---
title: "Networking"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Lars Hjalte on 2007-02-08
Here's the latest in the continiously growing line of problems I've had since switching to linux. Any more and I might regret switching in the first place.

Earlier I've had a windows-network in my home consisting of one printer and two xp-computers conected to a router, which in turn is connected to a adsl-modem. For my linux installation I hooked a third computer up to an empty slot in the router and immediately was able to access the internet. But after the installation was finished and I rebooted the system it was unable to comunicate with the network. I've been told that this is a common problem and easily fixed but after taking suggested actions there has been no change. In fact, the entire network has collapsed leaving only one computer with internet connection and none with printeraccess. Therefore I've decided to create a new network from skratch, which I've never done before and there are litteraly no guides that I can understand explaining how to set up, configure and use a shared windows and linux network.

As a matter of fact I'm not very experienced in networks all together but the issue badly needs resolving and since the network's som messed up I thought this might be the place to turn to.

---

### Post by kb3hkg on 2007-02-08
Which parts of this are you trying to get help with, just getting the linux machine connecting or building a new network?

to get linux up try running dhclient in a terminal.

As for setting up a network, what questions do you have exactly?

---

### Post by punx45 on 2007-02-08
what were the suggested actions that crippled the network?
was the printer networked, or being shared via one of the networked computers (i.e. was the printer wired directly to the router, or was it wired to one of the PCs?)
do you have DHCP enabled on the router? did you set up the linux machine to get its network connection or did you configure it manually?

as far as the physical setup of the network, it sounds like everything is done correctly already.

---

### Post by Lars Hjalte on 2007-02-08
The first thing is to get the network up and running and then I wish to be able to connect the linux-machine to it for updates, software installation and so on.

As for the previous network; everything and I do mean everything was running through the router. The router is running dhcp and the actions I took was was to edit the network called "eth0" on the linux machine, changing its settings from static IP to dhcp. Why that crippled the network I don't know. My guess is it wasn't very stable to begin with. During the installation process all I did was connect the computer to the network via tp without making any adjustments.

The questions I have are these:

1. Can my network be saved or is it better to give it a fresh start?
2. Which changes will I have to make to the individual parts of the network?
3. Will there be any complications between the linux and windows computers, and which?

---

### Post by aberry5555 on 2007-02-08
to be honest there should be no settings on your router that would affect your network, and the router should literally be plug and play so I severly doubt that plugging in your linux PC had that effect, unless the PC had a faulty network card. 

By the sounds of it it's a problem with the router, try restarting it or setting it factory settings, I don't think it's anything to do with the settings on the PC as settings on one PC has very little effect on another unless one of them is the domain server.

---

### Post by punx45 on 2007-02-08
the the linux machine started out with a static IP?   what IP did you give it? if that IP conflicted with something else on the network that may have broken something.

now that you have the linux machine configured to connect with DHCP i would power cycle the modem and router and reboot all the machines.   shut down all the computers, then unplug the router and the modem, and wait a minute.   when you bring everything back up start with the modem, then the router, then each of the computers.   i know its a pain, but sometimes with home networks thats all that works.

I suppose that would answer question 1.
2. everything was working before, so you shouldnt have to change anything other than restarting it all.
3.if you are planning on sharing files between computers you have a few more steps to take after you get the network back up.  Read up on SAMBA.   you also might have to do some configuring if you want the linux to use the printer, however, I have not owned a printer in quite some time, so I am of no help there.

---

### Post by Lars Hjalte on 2007-02-08
Thanks a bunch. I pulled the voltage to the router and when I shoved it back in all problems were resolved for now(please don't let there be any others).:KS

---


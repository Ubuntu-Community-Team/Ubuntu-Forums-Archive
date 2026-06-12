---
title: "Wireless Internet Not Working..."
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by chris_knows on 2006-06-25
I just got Ubuntu (Not sure which build exactly) and I'd like to switch to make that my main operating system, but I can't connect to the internet. I'm using a D-Link Di-524 Wireless Router, and when I put the settings in for the internet, it still doesn't work...

Thanks in advance for any help.

---

### Post by jennie on 2006-06-25
Ubuntu might be trying to use a built-in driver that doesn't really work.  If so, you'd need to blacklist that driver and use ndiswrapper to set up the right one.

Check out this site for instructions [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by e_james on 2006-06-25
I haven't used D-Link myself but there are several seperate steps in using wireless routers. 
1. the router needs to connect to the internet using ADSL. There are settings for this from your ISP. Have you used this router with another OS e.g. Windows XP?
2. The PC connects to the router. This can be wired or wireless. If you are testing a new router a wired connection eliminates some of the possible complications which might block your access. I would expect that connecting a Linux PC to a router by wired ethernet would be almost automatic. You can test this connection by communicating direct with the router from a web browser e.g. Firefox. The usual way is to enter the URL [http://192.168.0.1](http://192.168.0.1) (sometimes 192.168.1.1). The router instructions should tell you this.

Setting up the wireless connection is probably the most difficult part since you now have to get the wireless adapter connected to the PC working. Is this your problem?

---

### Post by chris_knows on 2006-06-25
I've used the router for about 6-7 months with Windows XP without problems...I'll try going to 192.168.1.1 and the website and tell you guys what happens. Thanks for the help :D

---

### Post by chris_knows on 2006-06-25
Sorry for the double post, but I don't know what to do...I'm in Linux right now (using the ethernet cable) and I realized what the problem was...I just had the same problem with Windows XP (When I was installing Linux, I messed up with the partitions and had to re-install windows...A couple of times, until i figured out how to partition lol...And I needed the CD with the drivers...So basically, Wireless internet isn't installed on Linux and I can't find the drivers anywhere...

Oh, BTW turns out I'm using Ubuntu 6.06 LTS! lol...

---

### Post by e_james on 2006-06-26
I assume from what you have said so far that your problem lies with the wireless adapter. You haven't said what model but I am guessing that it is also D-Link which means I know almost nothing about it. Here are some of things I have learnt so far (I'm new to Linux myself).

Linux and Wireless can be tricky. Sometimes you can be really lucky and it works right away. (Go to System --Administration -- Networking and you should find an application that is roughly the equivalent of Windows Network Connections. It may be that all you need to do is activate the relevant connection.) Sometimes you can be really unlucky and when you activate the connection Ubuntu crashes (reset button).
I picked up a tip a few days ago about installing a management application ([http://ubuntuforums.org/showthread.php?t=125150](http://ubuntuforums.org/showthread.php?t=125150) is similar.). It enabled one of my adapters (the Intel one built into the laptop) but not the other (Netgear WG511 pcmcia). It seems, if necessary, that you can often enable your adapter using your Windows drivers and an application called "ndiswrapper". Probably my next exercise.

Linux and USB can be tricky if the hardware in question doesn't look like a disc drive.

Linux and USB and Wireless networking is tricky squared. I have 3 different USB wireless adapters. 2 of them are not even noticed and 1 doesn't work. (See "crash" reference above).

---


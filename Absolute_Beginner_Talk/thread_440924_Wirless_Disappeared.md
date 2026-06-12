---
title: "Wirless Disappeared"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-12
My N1 wireless adapter has vanished from my network settings window.  I can still detect it in my Hardware Information - device manager.  If I look at Admin-Windows Wireless Drivers, the driver is still there, and, if I try to reinstall the driver from the Belkin driver CD, Ubuntu informs me that the driver is already installed.

This adapter worked flawlessly for an entire week, and, then, it just disappeared.

I see many other posters with similar problems, but, I don't see many solutions.

I hope someone can help.

I am running 7.04 and installed the driver by using Automatix2 to download/install NDISWrapper.  After encountering this problem, I used Automatix2 to uninstall, then, reinstall the wrapper, so, I don't think this has anything to do with Automatix2.

Suggestions would be most appreciated.  I use this machine when I am away, and, without a wireless adapter to get to the 'net, Ubuntu operates with a couple of arms tied behind its back.

Caruso

---

### Post by carusoswi on 2007-05-12
BTW, the adapter works fine when I boot into XP.

---

### Post by jiminycricket on 2007-05-12
Try this guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-8ff53b9f3168f7b274ba0934a76c0cc84a846ecb](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-8ff53b9f3168f7b274ba0934a76c0cc84a846ecb) 

and report back here

---

### Post by carusoswi on 2007-05-12
Jiminy:
The good news is that running 'modprod' brought my N1 wirless adapter back to Ubuntu life.  The bad news is that I cannot seem to get it to communicate with the router.  Everything is working fine in XP, but, in Ubuntu, the router remains unreachable.  I'm working my way through the steps in the link that you provided.  Any additional help you can give would be apprecited.

Caruso

---

### Post by carusoswi on 2007-05-12
I am stumped.  
My wireless adapter can see the router.  I have tried setting my key, changing from static IP address to DHCP, etc.

No joy.

Any suggestions would be appreciated.

When I run 'iwconfig' it shows that there are no associations for my adapter.  

Argh.

My 'puter is a lame duck without a wireless Ubuntu connection.

Caruso

---

### Post by carusoswi on 2007-05-12
Ok, I downloaded and installed GTKwifi to see if that would help expose the problem I'm having this morning.  Here is what it reports:

FF:00:FF:00:FF:00 / managed
Warning: Unknown AP mode on network 'TPZV7 Verizon' (00:15:05:EE:31:E3)
Warning: Unknown AP mode on network 'linksys' (00:14:BF:9C:7A:D0)


The two routers are mine.  liniksys is powered on, but not plugged into any computer and not in service.  TPZV7 Verizon is the one I'm trying to connect to.  My computer is wired to that router via Ethernet cable, and I am also trying to get my wireless to work with it.  The wired connection is working fine (I'm using that connection now), and both connections are working fine in XP.

Cannot figure out what is going on with the wirless in Ubuntu.

Can someone tell me what the above messages mean?

What to do about them?

Thanks.

Caruso

---

### Post by carusoswi on 2007-05-12
Here's what 'iwconfig' returns on my system:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Why no signal?  

I got that GTKwifi to run - it doesn't look right on my screen, but, it, too shows that there is 0 connection signal strength.  That doesn't make sense.  When I go into Network, the strength of my signal shows at 100%.

I configured this same wireless unit on XP, and XP doesn't care if I type the key in all caps or lowercase, and I did connect, so I know I'm typing the correct key (it's the only one I have).  Even if I didn't type the correct key, I would expect signal strength to register.

Can anyone help me figure out what is going on?

Thanks.

Caruso

---


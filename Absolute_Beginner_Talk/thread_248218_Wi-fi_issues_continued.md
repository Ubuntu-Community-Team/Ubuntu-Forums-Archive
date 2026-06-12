---
title: "Wi-fi issues continued"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by ctlw83 on 2006-08-31
Ok,

  I attempted about 5 different instructions to use ndiswrapper to get my broadcom wireless card to work.  Then, I figured that because I was running ubuntu 5.1 I should upgrade to dapper and it might help, it didn't.

then I folled the intructions on [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")and I got a new network device, that detects wireless networks but, doesn't connect to them or the internet.  The light for my wireless device doesn't turn on and dchp (or dhcp, whichever it is) is turned on...

I tried doing the ndiswrapper thing again and that did nothing to fix that problem.

So to summarize:
*Tried Ndiswrapper without success on 5.10
*Upgraded to Dapper
*Installed and used bcm43xx-fwcutter and installed using the proper driver sys file
*Got a new network device eth1 that says it is a wireless connection, displays different local wireless connections but, doesn't connect to them or if it does, not the internet.
*Tried ndiswrapper again with no success

Any ideas??  Any help after about 20 hours of working on this would really be appreciated.

Just so you know I am running this dual boot off of an Acer Aspire 3000.  I've read all I can on the issues the wireless card /chip on this computer and how to fix it so it will work.  Please help if possible...

God Bless,
Chris

---

### Post by kidders on 2006-09-01
Hi Chris,

It sounds like you've done the hard part already... I once tried exactly the same thing on my Mac with Gentoo Linux and it took me *forever* to get it right!

It might be wise to forget DHCP for a while and keep things simple, until you know what works and what doesn't. Also, you should turn off WPA or any other wireless security you're using at the access point. Basically, switch off anything that might break or cause trouble, and once you have network access, turn them back on one by one.

You might have more luck that way, I think. Follow your instructions (wherever you're getting them from) for configuring a security-less connection and try to manually assign yourself a network address. If you can so much as ping another computer on your network ... or even the access point itself ... you're in business :)

Any help?

---

### Post by TFX360 on 2006-09-01
> **ctlw83 said:**
> Ok,

  I attempted about 5 different instructions to use ndiswrapper to get my broadcom wireless card to work.  Then, I figured that because I was running ubuntu 5.1 I should upgrade to dapper and it might help, it didn't.

then I folled the intructions on [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")and I got a new network device, that detects wireless networks but, doesn't connect to them or the internet.  The light for my wireless device doesn't turn on and dchp (or dhcp, whichever it is) is turned on...

I tried doing the ndiswrapper thing again and that did nothing to fix that problem.

So to summarize:
*Tried Ndiswrapper without success on 5.10
*Upgraded to Dapper
*Installed and used bcm43xx-fwcutter and installed using the proper driver sys file
*Got a new network device eth1 that says it is a wireless connection, displays different local wireless connections but, doesn't connect to them or if it does, not the internet.
*Tried ndiswrapper again with no success

Any ideas??  Any help after about 20 hours of working on this would really be appreciated.

Just so you know I am running this dual boot off of an Acer Aspire 3000.  I've read all I can on the issues the wireless card /chip on this computer and how to fix it so it will work.  Please help if possible...

God Bless,
Chris

I added this script for easy creating of the output.

It generates what I need to help you to output.txt.

You can paste this output in this thread.

Copy the file to you home directory or where ever you want.

The file -> [broadcom]("http://home.casema.nl/d.sluijter/broadcom")

open a terminal and go to the folder you downloaded the file do:


```
sudo chmod +x broadcom; ./broadcom
```


Copy and paste the contents of output.txt here in the forum. Gedit starts automatically showing you the output.txt. Copy & Paste!

---

### Post by ctlw83 on 2006-09-01
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
eth1      IEEE 802.11b/g  ESSID:"thecornercoffeehouse"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:CA:47:10  
          inet addr:192.168.1.78  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feca:4710/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37051 (36.1 KiB)  TX bytes:5094 (4.9 KiB)
          Interrupt:169 Base address:0x1800 

eth1      Link encap:Ethernet  HWaddr 00:14:A4:35:64:3E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:5 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:311 (311.0 b)  TX bytes:4368 (4.2 KiB)
          Interrupt:4 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:310260 (302.9 KiB)  TX bytes:310260 (302.9 KiB)

No drivers installed
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

iface wlan0 inet dhcp
wireless-essid 3045 3354
wireless-key s:ed5fba733f7a88e28f31039b57

auto wlan0

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid thecornercoffeehouse

auto eth1


Ok, there are a couple of things even I can pick up from this file.  One, I have the card trying to connect to 2 ESSID's at once, one at work and one at the hotel.  Not sure how to change that..

Two ndiswrapper doesn't think my driver is there.  However, when I go to install it, it says driver already installed use -e to remove but, it also says the driver is invalid when I list it.  This is the driver I downloaded from the manufacturer's website!

Third, the light for my wirless card does not come on, despite the fact that the card seems to be reading local wireless connections, is something wrong there?

Fourth, Acer Aspire laptops suck and I am never buying one again!

And I end with a question.  Is it possible to have ubuntu automatically detect and select the closest open wireless conection without any fuss?

Ok...any and all directions/advice will be followed to the letter...

Thanks for your help everyone!

God Bless,
Chris

---

### Post by insightnsound on 2006-09-01
If you have the Broadcom 4318 chipset then you need to give this a try.  I messed around with my Linksys wpc54g ver3 for awhile finally did a fresh install and followed these instruction with great success.  I could have kicked myself when it turned out to be this easy.

[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)

---

### Post by TFX360 on 2006-09-01
First, install the correct driver. If ndiswrapper says it's invalid it's invalid. Your wireless card **IS NOT** wlan0 it's eth1 as you can see. So the config in ```
/etc/network/interfaces
``` won't work not now not ever.

The output of ```
sudo ndiswrapper -l
``` must be:

driver present, hardware present.



Success!

---

### Post by ctlw83 on 2006-09-03
The tutorial insightnsound posted seemes to have worked a little.  At least now the light for my network card is on.  Stillo no internet via wi-fi though.  Will re-boot and try again...

---


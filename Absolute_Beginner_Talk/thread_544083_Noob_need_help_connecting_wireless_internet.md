---
title: "Noob need help connecting wireless internet"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by me345 on 2007-09-05
So I just installed ubuntu to an old compaq presario 7360.  These are the specs:
500 mhz
512 MB Ram
8 gb hard drive

I am using a linksys wireless G (WMP54G) wireless card to connect to a linksys router (WRT54G).  My laptop connects fine which is running windows xp, but my desktop with ubuntu will see the network but won't connect.  I put in the passcode, but it still wont connect.

I am brand new to this and tried finding the answer in the forum and couldn't.  Please help!

Thanks

---

### Post by Crafty Kisses on 2007-09-05
> **me345 said:**
> So I just installed ubuntu to an old compaq presario 7360.  These are the specs:
500 mhz
512 MB Ram
8 gb hard drive

I am using a linksys wireless G (WMP54G) wireless card to connect to a linksys router (WRT54G).  My laptop connects fine which is running windows xp, but my desktop with ubuntu will see the network but won't connect.  I put in the passcode, but it still wont connect.

I am brand new to this and tried finding the answer in the forum and couldn't.  Please help!

Thanks

You probably have to use a NDISWrapper, the following link may help you:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Hope this helps. :)

---

### Post by TALLandNcharge on 2007-09-05
Try changing the option from automatic to TKIP.  Let me know if that works.

---

### Post by kevdog on 2007-09-05
Can you post 

lshw -C network

How did you install the drivers??

Are you trying to use WEP or WPA?

Can you connect to an unencrypted network??

---

### Post by me345 on 2007-09-05
Thanks for the quick responses!  Here is the result from lshw -C network:

WARNING: you should run this program as super-user.
  *-network:0
	description: Wireless interface
	product: RT2561/RT61 802.11g PCI
	vendor: Ralink
	physical id: 9
	bus info: pci@00:9.0
	logical name: ral
	version: 00
	serial: 00:1c:10:6a:3c:74
	width 32 bits
	clock: 33MHz
	capabilities: bus_master cap_list ethernet physical wireless
	configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=66 multicast=yes wireless-RT61 Wireless
	resources: iomemory: 41200000-41207fff irq:5
  *-network:1
	description: Ethernet interface
	product: RTL8139 Ethernet
	vendor: D-Link System Inc
	physical id: a
	bus info: pci@00:0a.0
	logical name: eth0
	version: 10
	serial: 00:05:5d:46:41:77
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master cap_list ethernet physical
	configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=66 maxlatency=64 mingnt=32 multicast=yes
	resources: ioport:1800-18ff iomemory:41100000-411000ff irq:10
-----------------------------------

Also I am not sure how to change from automatic to TKIP but i will try to find it and report back.

Thanks!

---

### Post by pgar23 on 2007-09-06
Check out this [HOWTO]("http://ubuntuforums.org/showthread.php?t=225206&highlight=javajake")
it is concerning linksys adapters and routers.
If you have any questions, just ask him. Javajake is very prompt and well respected pertaining to wireless networks, I would say.

---

### Post by me345 on 2007-09-06
Weel i've tried the ndiswrapper, but I don't know if I am using the correct windows driver.  I tried to install the driver from the windows cd by copying it onto the hardrive and using the ndiswrapper graphical interface as the article stated, but nothing shows up in the section that says "currently installed drivers" and when I opened a terminal and typed "ndiswrapper -l" nothing happened.

I'll try the how to guide next.

Thanks again for all of the help!!

---

### Post by me345 on 2007-09-07
Well I still have not been able to get this to work.  Here is where I'm at:

I tried to follow the instructions posted here: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

The problem I am having is that the driver used in this guide is out of date and the new file is: IS_Linux_STA_6x_D_1.1.1.0.tar.gz

In the step that says "compilation of the module" I can not get it to work with the new file name.  I may be putting in the wrong command (I am brand new to this so it is highly likely), but I also do not know if the file is in the "Current directory" (the file appears on the desktop).

Can someone please help me to get past this step so I can know if this will work?

Thx!

---

### Post by me345 on 2007-09-07
Well  I have figured out how to run the instructions with the new driver and got all the way through the instructions, but there is still a problem.  The first thing I noticed is that interfaces screen that opens up states this:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
aface ethl inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


The instructions say though that the screen should read:
iface ra0 inet dhcp
auto ra0

Everything before this step seemed to go smoothly though.

The second problem occured when I put in the last command: sudo ifup ra0

I get back this: Ignoring unknown interface ra0=ra0

If anyone knows what went wrong please help!

Thanks

---

### Post by me345 on 2007-09-08
bump

---

### Post by me345 on 2007-09-09
Bump

---


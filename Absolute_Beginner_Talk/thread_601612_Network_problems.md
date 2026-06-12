---
title: "Network problems"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by rlmcvey on 2007-11-03
I have installed Ubuntu on my Aspire 5000 running Windows XP.
I installed Ubuntu on a new unused partition and boot Ubuntu from that partition.

Problem – Setting up web connection.
I have tried the following -

System pull down menu has – Administration – Network and Network Tools 
						NOT Networking 
Selected Network  
	Network Setting screen
		Wireless
		Wired
		Modem
I have a wireless modem but am using dial as no wireless is available here

I selected Wired – Properties 
	Received screen “Settings for interface eth0”
		Selected Automatic Configuration (DHCP)

Step 5 in the manual says to click Activate/Deactivate – I don't seem to have this option?
	I selected OK.
		Then selected CLOSE for the Network Settings screen.

Selected FoxFire Browser
	Received - Welcome to Ubuntu 7.04, Feisty Fawn!

Selected Getting Started
	Received - Firefox can't find the server at en-us.[www.mozilla.com](www.mozilla.com)
	
1. Check the address for typing errors such as
    ww.example.com instead of [www.example.com](www.example.com)
    (this is ok)
2.  If you are unable to load any pages, check your computer's network
    connection.
    (can't check this)
3.  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.
    (don't know how to check this?)

ANY HELP WOULD BE APPRECIATED. - Bob McVey

Executing lspci -v in the terminal mode lists the following for my model -

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])

	Subsystem: Acer Incorporated [ALI] Unknown device 0083

	Flags: medium devsel, IRQ 17

	I/O ports at 1000 [size=256]

	I/O ports at 1c00 [size=128]

	Capabilities: <access denied>

---

### Post by n3tfury on 2007-11-03
i'm not sure how to setup a dialup modem since i can't remember the last time i've even used one, but have you looked here?

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---


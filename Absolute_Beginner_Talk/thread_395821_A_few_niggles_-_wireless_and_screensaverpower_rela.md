---
title: "A few niggles - wireless and screensaver/power related"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by adamr on 2007-03-28
My Edgy install is working just fine, but I have a couple of little niggles I'm hoping some of you good folks can help me with.

[LIST=1]
[*]Wireless network browsing - I can do it from the terminal in essence, but what I'd like is a decent wireless network browser, something similar to the Windows Zero configurator would be ideal. I know Gnome has its own network manager, but I also seem to remember reading something saying that the Ubuntu team wasn't going to fix the wireless browsing until the next big release. Any suggestions?
[*]Wireless network stability - Sometimes I'll leave the computer for a few hours and the wireless connection is effectively dead. It still shows as connected, but there's no traffic. The quickest way I've found to get it working again is System > Administration > Neworking and to then hop in and out of the wireless properties, disabling and then re-enabling the interface. Perhaps coincidentally, I cannot connect as a DHCP client to my router, whereas the Windows machines in the house do so just fine.
[*]Screensaver/power - I have a screensaver set, which works most of the time, but sometimes (approx 50% of the time) when I come back to the PC, the monitor's power is in standby. Under the Power Management settings in Gnome it's set to be always on, 
[/LIST]

If anyone can point me in the right direction for any of these I'd be very grateful.

p.s. I'm using a broadcom wireless PCI card and got it working by ripping the firmware from my windows drivers, not using the wrapper.

---

### Post by Feenix3k on 2007-03-29
What is the chip set on the Wireless card?
this code will give you the information:

lspci | grep Broadcom\ Corporation

I get  0000:02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)  on my laptop

---

### Post by adamr on 2007-03-29
I'll have a look when I get home from work. The wireless works, it just tends to not work properly after periods of inactivity. The lack of working DHCP does worry me though. I'm wondering if running the wrapper driver is the better way to go.

---

### Post by adamr on 2007-03-29
Ok, as promised..

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

As I say, it 'works' just not properly it seems. Lack of DHCP support is my biggest annoyance.

---

### Post by Feenix3k on 2007-03-29
wifi radar should help as your network control program. It sets the  wap/dhcp when you set up your connections on the computer.

---

### Post by mkjarema on 2007-03-29
> **Feenix3k said:**
> wifi radar should help as your network control program. It sets the  wap/dhcp when you set up your connections on the computer.

do you think this would help with a BCM4318 also?

---

### Post by Feenix3k on 2007-03-29
This is the how to I used for my bcm4309, but it is the set up for bcm4318. This should get your card set up and with wifi radar you will have the abilaty to set the router as wep or DHCP




 HOWTO/SCRIPT: Broadcom 4318 Wireless Cards 

About

This HOWTO is for people who have a Broadcom 4318 Wireless card in their laptop. This card can sometimes be a bit  difficult to setup, so I have provided a working method (for me, anyway).

To check if you have a Broadcom 4318 Card, open up the terminal (click the Applications button, then Accessories, and then Terminal) and run (just copy and paste the code from the code boxes throughout the HOWTO [in the terminal, this is done by right click anywhere and clicking paste, ctrl+v doesn't work])

Code:
lspci | grep Broadcom\ Corporation
If your output looks similar to 
Code:
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
or you can see the string BCM4318 in the output, then this should work for you.

Please note that this was really designed to be run on a very fresh install, right after Ubuntu has come up for the first time. It is mostly likely to work then. If you have tried other attempts at making this card work, I have no promises for you, but it only takes two minutes, so it is worth a shot (most people can get it to work, even on a not-so-fresh install).

The point of this HOWTO is to make it as simple as possible (not to educate people - if you want to know how this works, open the script and read it) for people who have just installed Ubuntu for the first time, so I wrote a script and have provided a set of drivers that worked for me. Not all drivers will work with ndiswrapper, so please use the ones I have provided.

The script requires no internet connection after it is downloaded...all required files are on the CD you installed Ubuntu with, and the package manager should recognize this.

If you post for help, please post the log file, which can be found on your Desktop after you run the script.

Process for Dapper and Edgy (see Fiesty in troubleshooting)
1.Put the CD that you installed Ubuntu with in the CD drive.
2.Download this file to your Desktop (the Firefox default, so if you haven't changed it, that's where it went/will go).
3.Open a terminal (click the Applications button, then Accessories, and then Terminal)
4.Change the current directory to the desktop (copy and paste the following commands exactly into your terminal by right clicking anywhere on the terminal and clicking paste)
Code:
cd ~/Desktop
5.Extract the compressed file
Code:
tar -xf bcm4318*.tar.gz
6.Run the script, which will install ndiswrapper on your system, and set it up.
Code:
sudo ./ndiswrapper_setup
7.Use the internet (you will have to open the System menu at the top of the screen, go to Administration, and then click Networking. Configure the interface eth1 or wlan0, and connect to your wifi network)
8.If you are an Acer user, you will need to use the acerhk driver.
9.If it doesn't work, reboot.
10.If that doesn't work, read the troubleshooting section below.
11.If you still can't make it work, try reading this post by The Raven, which is so long I can't even fit it in here without doubling the length of the post

---

### Post by adamr on 2007-03-30
I noticed wifi radar doesn't actually do a lot (certainly under Edgy). I can see both of my wireless networks (they're on different channels), but can't actually do anything with either. Choosing one and clicking Edit does nothing.

---

### Post by Feenix3k on 2007-03-30
> **adamr said:**
> I noticed wifi radar doesn't actually do a lot (certainly under Edgy). I can see both of my wireless networks (they're on different channels), but can't actually do anything with either. Choosing one and clicking Edit does nothing.

If it is the fiirst time use click connect , then the dilog open to set up the settings. EDit is use to change settings after they are set.


Wifi Radar works better for me the the gnome network manager

---


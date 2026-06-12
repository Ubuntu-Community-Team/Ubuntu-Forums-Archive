---
title: "Newb: Wireless connection [Airforce One card; Unknown make)"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by lucky-one on 2008-02-28
Installing Ubuntu for the very first time.
No Linux Experience at all. (Nor UNIX or any other *NIX type of system)
Got this forum recommended.

**Problem description**
My wireless card seems to detect fine. It is set to "Roaming Mode" .
No wireless networks appear from the network icon, just the wired one. 
I searched the forum, but found no useful fix to my problem. Sorry if i missed it. 

It seems i should post the output of "lspci", so i did. Be warned i have no idea what it is.

> 00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)


---

### Post by TheDilettante on 2008-02-28
> 00:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

your card is made by broadcom; specifically its a BCM4318.  Ubuntu detected it because it comes with a restricted driver for this family of chips; the driver is called BCM43xx.  What you should google and check up on is whether Ubuntu is correctly ID'ing the chip, and whether the BCM43xx supports your specific model (this is not always the case, as the Atheros 5k, for example, supports 5005 and 5006, but misidentifies 5007 as 5006.)

---

### Post by plinydogg on 2008-02-28
lucky-one,

I'm pretty sure I have the same card. The first thing you'll need to do is enable the restricted driver for the card (Ubuntu is all about free, open source software. The driver for your card doesn't fall into this category and so you have to go out of your way to enable it). Do so by going to the System->Administration->Restricted Driver Manager and enabling it (it should be call3ed "Firmware for Broadcom 43xx chipset family). 

If it doesn't work after that, then you may have better luck installing a program called WICD  (I use it). It will replace the default "Network Manager" program and works better for many people (warning: if you install WICD and it doesn't work, you'll have to reinstall Network Manager). 

To install WICD, I think you can just open up the terminal (Applications->Accessories->Terminal) and type:

sudo aptitude install wicd

I think that's what you do anyway...

Good luck!

---

### Post by spamzilla on 2008-02-28
Wicd isn't in the repo's, so sudo aptitude install wicd won't work. 

Google 'Wicd' and download the latest .deb from their site.

---

### Post by TheDilettante on 2008-02-28
for clarity:  you also have to uninstall Network Manager to make Wicd work.  the two conflict.

---

### Post by clb137 on 2008-02-28
HI,

I have the same card, 

Have you enabled the restricted drivers? then downloaded from the internet the driver for you card? this comes up automaticly when you enable the driver, you should then be good to go.  I Did NOT load my windows .INF file.

Good luck

Clint

---

### Post by lucky-one on 2008-02-29
sorry I'm responding late, had some troubleshooting

I've tried to run Wicd, but didn't work. Then i was unable to connect at all. I had to reinstall. This is now a "clean" install.

I've also downloaded ndiswrapper, and installed it, i don't know if it is an application of something else.  

Still no wireless networks appear in the network-manager icon. 

This is where I'm stuck, and with no Linux-Management experience, i rely on your advice. 

p.s one of friends just enabled "roaming mode on my wired net work", as opposed to DHCP and suddenly i couldn't connect to my wired network, so i had to reboot my computer and then it worked.

---

### Post by anewguy on 2008-02-29
Let's try to undo what you did so far, so we can start on a clean slate.

In a terminal window:

sudo ndiswrapper -l  (lower case "L" for "list")

if anything is returned from the above, remove it using:

sudo ndiswrapper -e xxxxxx (where xxxxxx is the name returned above)

Repeat the above until nothing is returned. 

Now let's move on to installing your driver again:

copy the driver files (the .inf and .sys files) to your desktop)

In a terminal window:

cd ~/Desktop

sudo ndiswrapper -i xxxxxx.inf (lower case "I" for "install", the xxxxxx would be the name of your driver file - probably something like bcmwla5 or such for your card)

sudo ndiswrapper -l  (lower case "L" again - your device should show)

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Next we have to blacklist the dummy driver that came with Ubuntu:

cd /etc/modprobe.d

sudo gedit blacklist

add the following line to the end of that file:

blacklist bcm43xx

then save the file and exit

Next we need to be sure ndiswrapper starts at boot:

cd /etc

sudo gedit modules

add the following line to the end of that file:

ndiswrapper

then save the file and exit

Now, reboot - this is important!

After the boot, see if your wireless shows in the network icon.

:)

---

### Post by anewguy on 2008-03-01
Please let us know if this worked for you.  If so, please mark the thread as "solved".  If not, post back the results.

:)

---

### Post by lucky-one on 2008-03-01
> **anewguy said:**
> Let's try to undo what you did so far, so we can start on a clean slate.

In a terminal window:

sudo ndiswrapper -l  (lower case "L" for "list")

if anything is returned from the above, remove it using:

sudo ndiswrapper -e xxxxxx (where xxxxxx is the name returned above)

Repeat the above until nothing is returned. 

Now let's move on to installing your driver again:

copy the driver files (the .inf and .sys files) to your desktop)

In a terminal window:

cd ~/Desktop

sudo ndiswrapper -i xxxxxx.inf (lower case "I" for "install", the xxxxxx would be the name of your driver file - probably something like bcmwla5 or such for your card)

sudo ndiswrapper -l  (lower case "L" again - your device should show)

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Next we have to blacklist the dummy driver that came with Ubuntu:

cd /etc/modprobe.d

sudo gedit blacklist

add the following line to the end of that file:

blacklist bcm43xx

then save the file and exit

Next we need to be sure ndiswrapper starts at boot:

cd /etc

sudo gedit modules

add the following line to the end of that file:

ndiswrapper

then save the file and exit

Now, reboot - this is important!

After the boot, see if your wireless shows in the network icon.

:)

"No versions of ndiswrapper installed". How would i gain those drivers? I have no acces to a Microsoft partition, nor disc or anything. 

Thanks a lot for helping so far!

---

### Post by anewguy on 2008-03-01
Well, there are a couple of options that are easier than fetching the source and trying to compile it:

(1) Put the LiveCD in that you installed from (with Ubuntu running) and it should come up and ask if you want to open the package manager - answer yes.  When this comes up, do a search for ndiswrapper and its' utilities to see if it is included on that CD (I don't remember and I have long since loaned out that CD).  If it is there, just click and then apply.  If it wants to access the net, and you have no access to a wired connection to your wireless router, you will have to cancel.

(2) You could download the ISO image for version 6.x, burn it to a CD, then go into Ubuntu, insert that CD and then follow (1).  I know a version of ndiswrapper and its' utilities was on that CD originally.

If you can get wired access to your router or cable/DSL modem, then you could fetch it from the net using synaptic package manager.

If none of the above work, post back and we'll look at getting it somehow.  :)

EDIT::  This link will point you to a web page with instructions on installing ndiswrapper from source even without a network connection in Ubuntu, as long as you have access to another (or the same) computer with an OS you can get on the net with.

---

### Post by anewguy on 2008-03-01
I have grabbed the .deb from a 6.x LiveCD for ndiswrapper and will be trying to attach it.  You should be able to download it, copy it to Ubuntu (cd/floppy/usb drive, etc) and copy it to your desktop in Ubuntu.  Then just double click the file and I THINK (I haven't done this before so I'm sure) it will install, or at least come up with the package installer and you will just need to click on "install package".

Let me know if this works.  :)

---

### Post by cheezewiz25 on 2008-03-01
I have a related question that perhaps someone here would know the answer.  I am installing a Netgear 311 wireless card on a Pentium 3 900mhz computer installed with Gutsy (recently upgraded).  When I use the ndiswrapper windows driver installer under system and add the driver, I get the driver listed with "invalid driver!"  along with it. Has anyone had this occur?

---

### Post by anewguy on 2008-03-01
I've had that happen due to 2 things:

(1) Mistyped the name of the driver file

(2) Tried to install the .sys instead of the .inf file

The way I was able to clear it all up was:

(1) ndiswrapper -l to list the known drivers (even if bad)

(2) sudo ndiswrapper -e xxxxxx where xxxxxx is the name returned in (1)

(3) repeat (1) and (2) until an empty list is returned

Then, proceed with the driver installation again.  It usually works best to put the driver files on your desktop and then cd ~/Desktop before sudo ndiswrapper -i xxxx.inf  .  If the driver files are not in your default folder, and you instead specify a patch to them on the ndiswrapper -i, I have found that more times than not that causes problems and I have to clear everything and start again. 

Hope that helps! :)

---

### Post by lucky-one on 2008-03-03
> **anewguy said:**
> I have grabbed the .deb from a 6.x LiveCD for ndiswrapper and will be trying to attach it.  You should be able to download it, copy it to Ubuntu (cd/floppy/usb drive, etc) and copy it to your desktop in Ubuntu.  Then just double click the file and I THINK (I haven't done this before so I'm sure) it will install, or at least come up with the package installer and you will just need to click on "install package".

Let me know if this works.  :)

> **anewguy said:**
> Well, there are a couple of options that are easier than fetching the source and trying to compile it:

(1) Put the LiveCD in that you installed from (with Ubuntu running) and it should come up and ask if you want to open the package manager - answer yes.  When this comes up, do a search for ndiswrapper and its' utilities to see if it is included on that CD (I don't remember and I have long since loaned out that CD).  If it is there, just click and then apply.  If it wants toaccess the net, and you have no access to a wired connection to your wireless router, you will have to cancel.

(2) You could download the ISO image for version 6.x, burn it to a CD, then go into Ubuntu, insert that CD and then follow (1).  I know a version of ndiswrapper and its' utilities was on that CD originally.

If you can get wired access to your router or cable/DSL modem, then you could fetch it from the net using synaptic package manager.

If none of the above work, post back and we'll look at getting it somehow.  :)

EDIT::  This link will point you to a web page with instructions on installing ndiswrapper from source even without a network connection in Ubuntu, as long as you have access to another (or the same) computer with an OS you can get on the net with.


usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

 
installing bmc4318 ...
couldn't open bmc4318: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.


Maybe I'm just during it wrong, or could it be something else.

---


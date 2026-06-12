---
title: "wireless..."
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by colomob on 2007-12-02
i cant get my wireless card to work..it apears as if there arent any network. what can i do?

---

### Post by siciliancasanova on 2007-12-02
Well the first thing I would do when you have hardware issues is to type something like "need to install 'name of my hardware' on ubuntu gutsy gibbon"  or something to that effect.  Most often with hardware issues there is already an answer out there and will save you time.  Do that in google since google also index's ubuntu's forums.

make sure you are specific with the hardware, instead of typing in "linksys" also type in "linksys 54g" or whatever

---

### Post by nae5 on 2007-12-02
what kind of wireless card is it?

applications>accessories>terminal

```
lspci
```

paste output in forum or search the forum for that card

---

### Post by colomob on 2007-12-03
it says:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

---

### Post by nae5 on 2007-12-05
are you dual booting? windows and ubuntu?
laptop right? do you have backup ability for your music documents movies whatnot?

03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

this is your wireless card search the wireless forum for *ndiswrapper BCM 1390* and *Broadcom Compatibility List*, read n follow what other people with your card did.
     You're looking for the list that will tell you which windows driver files you need to use with ndiswrapper for your card.  Usually two: one .inf and one .sys. "Broadcom Compatibility List"

ndiswrapper "wraps" the windows drivers for wireless cards into ubuntu

Then you need a set of instructions to install ndiswrapper.  "ndiswrapper BCM 1390"  

i will post the one i used since i kept it, even though on my second clean install of gutsy on that comp the restricted drivers manager(which install bcm43xx-fwcutter, firmware) worked "out of box."

I think the command that you use to blacklist the old drivers isn't specific to each card but im not sure.  you might need the commands to blacklist the particular drivers not working for your card.  which shouldn't be hard to find.  (this is the first part of installing ndiswrapper, thatis, uninstalling the unworking drivers.)

There really are a whole lot of threads and posts on this topic but it can be hard if you don't know what to search for.  

ill search and get you a link to that list and then some instructions for your card, but i have some other things to take care of atm, so try it out for yourself. you can always backup and reninstall (infact, if youre new, you should have a way of backing up everything... someothertime..

---

### Post by nae5 on 2007-12-06
COURTESY OF :  Ayuthia 
Way Too Much Ubuntu
	  	
Join Date: Apr 2007
Location: Peterborough, UK
Beans: 245
Kubuntu 7.10 Gutsy Gibbon User
Gentoo User



ndiswrapper instructions
Here is the set of instructions that I have written up for ndiswrapper. If you want to go this route, please read it and if you have any questions, don't hesitate to ask. I can't guarantee that I can get you up and running, but I'll be more than happy to try.

Step 1:
Remove any prior installations:
sudo rmmod ndiswrapper
sudo ndiswrapper -e <driver> (if you know that you have installed a driver previously)
sudo apt-get remove ndiswrapper-utils

Step 2:
Grab the necessary packages for installing ndiswrapper:
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r` (the ` is a backquote not the single quote)

Step 3:
Download the most updated stable ndiswrapper from the ndiswrapper site ([http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net))

Step 4:
Download the driver and files (.inf and .sys files) needed for your chipset and place them in a certain directory like /home/user/drivers

Step 5:
Blacklist the bcm43xx driver so that it does not interfere with ndiswrapper:
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

Step 6:
Remove the bcm43xx module:
sudo rmmod bcm43xx

Step 7:
Change to the directory where you downloaded ndiswrapper and extract the file:
tar -xzvf ndiswrapper-<version>.tar.gz (replace <version> with the version downloaded--example: ndiswrapper-1.47.tar.gz)

Step 8:
Change to the extracted directory and prepare for isntall:
cd ndiswrapper-<version>
sudo make uninstall

Step 9:
Make the installation:
sudo make
sudo make install

Step 10:
Change to the driver directory and load the driver:
cd <driver directory> (replace <driver directory> with the directory where the driver is located--example: /home/user/drivers)
sudo ndiswrapper -i <driver.inf> (replace <driver.inf> with the name of the driver--example: bcmwl5.inf)

Step 11:
Check to see if the driver is loaded:
ndiswrapper -l

Step 12:
Load the module:
sudo depmod -a
sudo modprobe ndiswrapper

Step 13:
See if it all worked:
iwconfig
iwlist scan

Step 14:
Try to connect and if it works add the following:
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules

---

### Post by unknown user on 2007-12-08
I was unable to see any wireless networks with my HP NC6220 and I tried everything.  However, I found a post saying the another person had to go into their bios on boot up and reset their settings back to default.  I done this and now I have wireless.  

In saying that I now have no Bluetooth, where I had it before.  Looking at it this way I can put up with not having Bluetooth more than I can not having wireless.

Not sure if this will help, but worth a mention.:)

---


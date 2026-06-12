---
title: "Setting up BCM 4318 on a Presario V5000 with Fiesty"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by leefischer on 2007-05-10
I am new to all this so pease bear with me.   I have a wireless network at home that both my mac and my PC can see.  It uses WPA.   I just installed Ubuntu ffor the first time ever (7.04) and I can not get it to see the network.

The laptop has a small button on the case that allows you to easily turn the wireless card on and off.  This button dosn't appear to do anything since installing Ubuntu and remains in the "off" position, ie. not illuminated.  

When I go to System>Administration>Network, i can see an icon that says "wireless connection" and it says that "roaming mode is enabled"  

Questions:  
What is "roaming mode?" does that mean the system will scan for available networks?   If it finds one should it list that network somewhere or give me a prompt to join?   If so why can't it see my network?

Why is the little switch for the network card not working now?  Do i need some sort of driver for this?  If it does not work do you think that woud mean my card is not "on"?

Have a look at the info below  "*-network:0 DISABLED"  what does this mean?

Thanks in advance for help.  I am new to all this but a paitent learner.  Where should I start and can anyone help me through it please?

Lee

lee@Compaq:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:78:64:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0204000-c0205fff irq:21

---

### Post by Bachstelze on 2007-05-10
First, you need to install drivers for your card. Can you get the PC online with a wired network for downloading them ?

---

### Post by Kobalt on 2007-05-10
The roaming mode is a way to graphically manage over which network you'll connect, using the Network-Manager.
In order to get your card working you have two solutions : either using the windows drivers with ndiswrapper (which is the one I advise using) [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
or
the free drivers called bcm43xx [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by leefischer on 2007-05-10
I have another pc on line which I am using now.  I can download drivers with it.  Are you talking about linx drivers for the card?   What about the switch thing on the laptop?  Does that need a driver too?  I do have the original drivers for the card that I used in windows on a flash drive. Are they useful?

Lee

---

### Post by Uriel2006 on 2007-05-10
Hello I've the same card, and this topic was discussed times and times again, so i just reassume.

If you want to use the native driver bcm43xx:

1)Download one copy of 3.xx.xx drivers.
2)Use the bcm43xx-fwcutter utility to estract the firmware and then put it in /lib/firmware

If you want to use the native driver bcm43xx_mac80211

1)Download one copy of 4.xx.xx drivers 
2)Use the bcm43xx-fwcutter utility to estract the firmware and then put it in /lib/firmware

If you want to use ndiswrapper

1)use synaptic to install ndiswrapper
2)Put windows drivers coming with PC on disk.
3)ndiswrapper -i bcmwl5.inf

for more details, there are lot of messages on this forum, step to step :))



Uriel

---

### Post by leefischer on 2007-05-10
Got the driver,  having trouble installing the bcm43xx-fwcutter.  Where is this "package", is it on the install disk for Ubuntu or somewhere else?

Thanks for help.


lee@Compaq:~$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter

---

### Post by Bachstelze on 2007-05-10
It is not on the install disk of Ubuntu and even if it was, it needs to download the firmware from the Net so if you can't get your machine wired temporarily, it's a no go. You might be better off with ndiswrapper.

---

### Post by leefischer on 2007-05-10
Ok, I have the laptop with Ubuntu wired and am using it now.  I have downloaded the driver for my card ,bcmwl5.sys,  I I believe I now need to install the BCM43xx-fwcutter utility.   Where do i find this?    
When I open a terminal and run >sudo apt-get install bcm43xx-fwcutter  I get a message back saying >

lee@Compaq:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter

Does this I need to get some kind of install package from somewhere and put it in "E:" or something?

Cheers Lee

---

### Post by Kobalt on 2007-05-10
You need to download it (and maybe its 2 dependencies as well) from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then transfer it to the comuter on which you want to install it. Just double clic on the .deb file and it will install right away.

---

### Post by leefischer on 2007-05-10
Thanks to all.  My wireless is now working.

---

### Post by SoxFan on 2007-09-18
Did it fix the wireless network button issue as well?

---


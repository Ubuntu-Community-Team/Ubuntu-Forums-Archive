---
title: "Ubuntu?.I'm amazed, just need wireless!"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by svjenni on 2007-04-01
Hello all,

I'm hoping you guys can help me.  I installed Ubuntu yesterday using the text install as for some reason it kept hanging using live cd... all went well

... in fact much better than expected almost everything works straight out of the box!!

except wireless....doh

i have ethernet in built which is working. i also have a motorola pcmcia wireless card
the leds are dull on it and i can't seem to get it working

bear in mind i have not tried anything really, have pretty basic knowledge but am willing to try lots!

also, as i bought this laptop second hand i'm not sure if i also have an inbuilt wireless adaptor (its a toshiba satellite pro 4600)

will post some config on next post

---

### Post by svjenni on 2007-04-01
hope this helps:

jenni@ubuntu:~$ sudo lshw -class network
Password:
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:32:80:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.1.103 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:f7dff000-f7dfffff ioport:df40-df7f irq:11
  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@03:00.0
       logical name: eth1
       version: 03
       serial: 00:0c:e5:4e:a9:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:16000000-16001fff irq:11
jenni@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by johnny4north on 2007-04-01
which Ubuntu are u using 7.04 or others?

---

### Post by svjenni on 2007-04-01
sorry i'm on edgy eft 6.10 i think

---

### Post by Gina on 2007-04-01
Seems your wireless adapter is not directly supported (like many others).  The solution which usually works is to use your **Windows driver** .INF file and **ndiswrapper.**  Details are availably on this board and in many other places but if you can't find them come back.

---

### Post by johnny4north on 2007-04-01
i found a how to link - [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)  for the broadcom wireless :) .  thanks Ubuntu found more how-to set-up wifi card at - [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by johnny4north on 2007-04-01
your toshiba satellite pro 4600 should have Wifi if its cpu is p3 800Mhz are faster.  the older models dont.  i think ... thanks Ubuntu

---

### Post by svjenni on 2007-04-01
I just wanna say thanks......and sorry!

while waiting for answers I found the broadcom adapter page (thanks johnny) and lo and behold it works :) 

i am so happy, ubuntu is much faster than win 2k and everything works, in fact getting wireless set up was actually easier than windows.

I am seriously contemplating fully switching to ubuntu for my main computer now as I am so sick of windows crashing and running slowly,  thanks all for your help, and next time maybe i won't panic before posting!!!

---

### Post by jvc26 on 2007-04-01
:) good to hear you're enjoying Ubuntu, welcome to the community,
Il

---

### Post by nae5 on 2007-04-03
i have a similar problem on my dell inspiron 600m laptop. i tried using the .inf file from the driver in winxpsp2 that came with the pc using ndiswrapper. 

i had read on other guide posts that a **.sys** *as well as* a **.inf** file are needed, and that u only need the **.inf **file, well..

ndiswrapper only let me use the .inf file which seemed to load but would not work.  

so feisty beta was released and was supposed to have increased wireless compatibility. well it does . as soon as i installed it on the first reboot it found the card and the restricted drivers manager says i dont need anything. ubuntu cool.

however it will not connect to my unprotected home network with a mac address filter.(this pcs mac is allowed)  

i can post the ifconfig iwconfig sudo lshw -class network or any others (i cant make sense of alot of these but i know some)

i have to go connect to hard line to post them im on another comp now 
**plz help** wireless is the only thing stopping my main pc from ubuntu

---

### Post by finferflu on 2007-04-03
> **nae5 said:**
> i have a similar problem on my dell inspiron 600m laptop. i tried using the .inf file from the driver in winxpsp2 that came with the pc using ndiswrapper. 

i had read on other guide posts that a **.sys** *as well as* a **.inf** file are needed, and that u only need the **.inf **file, well..

ndiswrapper only let me use the .inf file which seemed to load but would not work.  

so feisty beta was released and was supposed to have increased wireless compatibility. well it does . as soon as i installed it on the first reboot it found the card and the restricted drivers manager says i dont need anything. ubuntu cool.

however it will not connect to my unprotected home network with a mac address filter.(this pcs mac is allowed)  

i can post the ifconfig iwconfig sudo lshw -class network or any others (i cant make sense of alot of these but i know some)

i have to go connect to hard line to post them im on another comp now 
**plz help** wireless is the only thing stopping my main pc from ubuntu
Note that when you install the driver using ndiswrapper, the .inf and .sys files need to be in the same folder. Actually sometimes you even need more files, so the best thing is installing it from the CD provided with the wireless card. I had problems installing my Netgear WG111 at times, because I didn't copy the right files in my folder, but installing from CD always works.

hope it helps...

---

### Post by Dual Cortex on 2007-04-03
**nae5**, see here for more info:
 [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
Make sure that all the driver files are in the same folder as the inf when installing,

---

### Post by nae5 on 2007-04-03
can i do this in feisty as well as one of the earlier ones? cuz in feisty it recognizes the card but it wont connect to wirls netwrk.

  so u mean (when i had done this in 6.06 or 6.10) that when i was supposed to tell ndiswrapper which inf file to use i browse to the folder it and other files are in and not to the actual bcwl5.inf file or whatever it was?

or do u mean that those other files only needed to be in the same folder?

**...skipto here..**i think the latter? u know now that i think about wut i did i tried to direct ndiswrapper to the windows partition of the same hd that was on the desktop... i was using the driver from the cd that was in the dell/driver directory so...  this is obviously wrong ?...

should i try to get it working in feisty or revert to 6.10 and use ndis?? btw thnx for ur superior knowledge

---


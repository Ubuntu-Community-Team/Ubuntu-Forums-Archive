---
title: "Wireless issue, BCM43XX......"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by nsimeone2000 on 2008-02-18
I have tried about 3 different methods to fixing my crappy Broadcom card, here are a list of things I have tried.

I tried reinstalling Ubuntu, (i know you are laughing, but it was entertaining for me too)

I tried the ndiswrapper method the drivers looked like they loaded fine, but nothing ever came of my wireless connection.

I also tried bcm43xx-Firmcutter, I extracted the bcmwl5.sys, and now I have a bunch of .fw files on my desktop and I am a little lost on this one, but it seemed really promising when I was able to get that bcmwl5.sys file working.

I did notice something wierd, don't know if it helps but i figured I would post it:
sudo lshw -C network
 *-network UNCLAIMED     
       description: Network controller
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:b6000000-b6003fff irq:255

The reason this seems wierd is because I have a HP computer, not a Dell.  Don't know if that makes a difference......

Anyone have any ideas on how to get this wireless card up and running?

lspci:
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
[COLOR="Red"]03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)[/COLOR]
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

Day 3 of Ubuntu, I am loving it, but this wireless card is kicking my butt.......Thanks for the help.

---

### Post by Golem XIV on 2008-02-18
I fixed my bcm43xx following the steps detailed here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Hopefully it'll help you, too.

Good luck!

---

### Post by nsimeone2000 on 2008-02-18
Thank you, I wish I had found that forum originally when I started working the issue, however, I cannot identify which BCM43 version I have, did you see where it says Dell Wireless card?  I am wondering if I read a different forum on accident and overwrote my drivers with a Dell one or something........

---

### Post by nsimeone2000 on 2008-02-18
Hrm, that walkthrough won't work for me because when I try to get ndiswrapper, it tells me that:
Selecting previously deselected package ndiswrapper-utils-1.9.
(Reading database ... 111069 files and directories currently installed.)
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.38-1ubuntu1_amd64.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--08:26:42--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 74.125.47.118
Connecting to boredklink.googlepages.com|74.125.47.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:26:42 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ndiswrapper-utils-1.9 (1.38-1ubuntu1) ...
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

Should I format and reinstall again?  Then try that link?

---

### Post by nsimeone2000 on 2008-02-18
I have been thinking in my head that maybe removing that bcm43xx-firmware cutter thing would be a good idea, I have located it /usr/bin, but I cannot delete it, I haven't been using ubuntu or Linux long enough to know the commands.  Can anyone enlighten me really quick?

---

### Post by mrsteveman1 on 2008-02-18
First of all, your cards chipset is a BCM94311 (99% sure about this).

Second, the drivers for this chip are very picky. Only specific firmware versions work with BCM43xx, and only specific drivers work with ndiswrapper.

I'm going to assume you are in fact using the bcm43xx driver (as opposed to the b43 driver in the new kernel).

the firmware cutter is relatively easy to use, and the wiki has pretty good instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy")

halfway down the page there are commandline instructions, but the GUI should work well.

If it doesn't, or if you have already done all this (different firmware versions, different windows drivers etc), post back and ill check which ones I'm using, because the ones i have work well.

---

### Post by kaginken on 2008-02-18
I too struggled with my BCM43xx on my Dell Latitude D610, but now Gutsy comes with the propriatary drivers manager thing that loads my driver up just fine.  That hasn't worked for you?

Before Gutsy came along, I found this python script worked very well.  It actually does it all automatically (downloads the windows drivers and firmware cutter, cuts the driver out, wraps it up and installs), the whole kit and kaboodle!!!  Give it a try:

[http://backports.ubuntuforums.com/showthread.php?t=405990](http://backports.ubuntuforums.com/showthread.php?t=405990)

Good luck and Godspeed!

---

### Post by fraser_m on 2008-02-18
This worked for me and I think I have the same card as you:

If you press ALT+F2, to get run application box up, and run "gksudo nautilus" type your password and navigate to /lib/firmware, then drag-and-drop your *.fw from your desktop there, then restart, that might work...

---

### Post by nsimeone2000 on 2008-02-18
Mr Steveman1

I am running Feisty, and I will not go Gutsy, here is why: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

I did but the bcm43xx firmcutter on here though, I logged in gkroot and nautilus and deleted it out of the usr/bin file.

Unfortunately when I try to run the scripts from here: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6)

None of them are working due to the bcm43xx firmcutter.  Thank you for confirming what I have in here though, I think that will help me narrow it down.

Kaginken, did you have to do anything else or did your wireless switch light come on?  I did this initially but nothing happened, is there a way to set up your eth0 and eth1 in terminal?


Fraser_m, tried that, unfortunately it didn't work.....

---

### Post by lswest on 2008-02-18
just a quick confirmation, yes, that card is a Broadcom 4311, it is recognized as a Dell card for whatever reason (i know, i have the same card :P).  however, mine's running using the ndiswrapper and the bcmwl5 drivers.  never tried the firmware cutter before, but i just wanted to clarify that it is in face a bcm4311^^ had me confused for a while too :P  (take my advice, don't ask HP what card is in your laptop...i got a list of 6 possible cards...)

---

### Post by nsimeone2000 on 2008-02-18
HP is a joke, I hate their customer service, and I love all the bandwidth they give to Linux customers when in search of their drivers, (that webpage is still loading, an has been for 2 hours)

I am thinking that maybe, just maybe I have to load the recovery disk, change the network configuration to wireless, I am thinking that this might fix the problem, since I can now hardwire anytime I need to thanks to my trusty router :lolflag:  

Are you running WEP?  because I am, I think that may be a problem as well, but not sure.

Thanks for all the responses though, lots of good information, you pick this stuff up quick!

---

### Post by nsimeone2000 on 2008-02-18
Alright, I have a fresh install so I will try that forum now,  Wish me Luck!

---

### Post by nsimeone2000 on 2008-02-18
> **Golem XIV said:**
> I fixed my bcm43xx following the steps detailed here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Hopefully it'll help you, too.

Good luck!

Awesome how to, it works great on a fresh install, I have the Wireless network in my network manager now.  I just have to figure out how to get it connected now, but when I saw that little orange light turn blue, I jumped up for joy.

Thanks again.

---

### Post by kaginken on 2008-02-18
nsimeone,

That link I sent you is all I required.  It may be what you need to do is (if possible) undo everything you've done so far (very difficult if you've done a lot) or reinstall ubuntu.  Then run that python script on a clean machine.

I know, I know...but it installs in about 30 minutes and a reinstall guarantees a good 'baseline' starting point.  Even if the solution I'm referring to doesn't work for you - you will want to know (for next time) exactly how to get that wireless working for you.  Best thing to do is install, get wireless working, and keep repeating that until it works.

Let me know once you get the link light on and I can point you in the right direction if you require any helpless in getting it connected.  Trust me, once the link light is on, the hardest part is over, it's a snap to get it talking to your router.

Above all - enjoy the process, there's nothing more satisfying than figuring it out, unless you've experienced shooting bullets at someone who's shooting at you.  :)

---

### Post by kaginken on 2008-02-18
you can disregard my last post about reinstalling  -  the time it took me to post that, you got your link light on, congrats!  Let me know if you need any helpless getting it to work...:)

---


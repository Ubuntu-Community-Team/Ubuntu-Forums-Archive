---
title: "TI 5-in-1 card reader problems (longwinded edition)"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Blue_Horseshoe on 2007-12-17
Hi guys, after spending some time (a few days) attempting to configure my card reader for basic SD functionality I believe I have exhausted my best resources, searching the forums and google. (I'm sure some wiseguy using his or hers mastery of syntax  will smack me with a "specific to my situation" how-to on the front page, and that would be wonderfull :) )

I've come across two in depth posts concerning this issue ( [#1]("http://ubuntuforums.org/showthread.php?t=420721&highlight=card+reader")  &[#2]("http://ubuntuforums.org/showthread.php?t=315497&highlight=card+reader") ) referencing older versions of ubuntu, and the([BerliOS]("http://developer.berlios.de/projects/tifmxx")) project page. ( I have trouble understanding some of the information here, information intended for more advanced users)  Working through directions on the two threads several times, with very little success, I typically end up reinstalling fresh. Owing this to my inability, or inexperience troubleshooting the new errors I've created tinkering around with drivers and settings, 

Following the directions in the above threads I was once able to mount the sd card, I then proceeded to edit a file, per the directions, loading the modules that made the reader functional at startup. To make the reader functional I also needed to use the "setpci hack" I thought my troubles were over, but upon reboot I lost card reader functionality, as well as introduced a myriad of startup errors, some of which made no sense at all, like an error related to an onboard ethernet jack, not present prior to my tinkering.

This may be where most of my problems come from,being new to linux, confused and overwhelmed by the new errors I create, I tend to reach for the live cd to reinstall rather than fix the mess I've created. Perhaps someone could post a link for me on backing up my settings and files so I can "break" without fear of wasting another 30 minutes reinstalling from scratch. I've been using a paper notebook to document to myself how I've installed/configured other devices and programs so when I manage to troubleshoot my remaining issues I can have a system suited to what I want, and expect from it. It just seems that there must be a better way than reinstalling several times daily :confused:

ANYWAY on to the dirty details.

System is an hp dv8309us laptop running Ubuntu (7.10  x86)   only looking for SD functionality (some other types of cards are not yet supported ) and no the card is not locked :)

pertinent terminal outputs

uname -r
```

2.6.22-14-generic

```

lspci (Not sure what you may need so I posted the whole 06:04.x address)
```

06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

/var/log/messages *note that this is a fresh install AND that the card mounted the first time I inserted it, after a right click>unmount, the reader is unresponsive and when inserted the card does not appear in /media or /dev 
```
Dec 17 00:12:48 laptop kernel: [83270.680000] tifm_core: MMC/SD card detected in socket 0:3
Dec 17 00:12:48 laptop kernel: [83270.816000] mmcblk0: mmc3:80ca SD01G 992000KiB 
Dec 17 00:12:48 laptop kernel: [83270.816000]  mmcblk0: p1
Dec 17 00:13:24 laptop kernel: [83306.884000] tifm0 : demand removing card from socket 0:3
Dec 17 00:13:26 laptop kernel: [83309.036000] tifm_core: MMC/SD card detected in socket 0:3
Dec 17 00:13:32 laptop kernel: [83315.524000] tifm0 : demand removing card from socket 0:3
Dec 17 00:13:34 laptop kernel: [83316.916000] tifm_core: MMC/SD card detected in socket 0:3
```

*[COLOR="Red"]PM me for if you need my var/log/messages, module.symvers or dmesg files, or _**someone let me know if these files are ok to post in a public area**_ (this forum) as an attachment. I'm not sure what's all in there and wouldn't want to compromise my security??? I dunno lo[/COLOR]l*

fdisk -l
card does not appear

a search of "filesystem" for "mmcblk0" returns no results

files located in /lib/modules/2.6.22-14-generic/kernel/drivers/mmc
folder/file
card/mmc_block.ko
core/mmc_core.ko
host/ sdhci.ko--tifm_sd.ko--wbsd.ko

current  lsmod | grep sd
tifm_sd                12808  0 
sdhci                  18828  0 
tifm_core              11652  2 tifm_sd,tifm_7xx1
mmc_core               28420  3 mmc_block,tifm_sd,sdhci

current lsmod | grep tifm
tifm_sd                12808  0 
tifm_7xx1               8832  0 
tifm_core              11652  2 tifm_sd,tifm_7xx1
mmc_core               28420  3 mmc_block,tifm_sd,sdhci

Background on me, for an idea how how dumbed down instructions must be for me to understand :lolflag:

I've been using linux for about 1 month, 3 weeks ago I promised myself I would avoid M$ like the plague, no inclination to play with Mr. Bill's monster ever again.

-comfortable loading and unloading modules, using modprobe & rmmod. 
-comfortable with and willing to research/learn new cli commands 
-iffy about scripting or configuring "load x module on boot/startup"
-beginner level linux vocabulary, basic overall understanding of what I'm trying to do here.
-most of what I've accomplished on the rest of the system was because of the wonderful support offered by the members of this forum.  
**-Wondering if some of the things I've been trying or files I've been using are kernel specific, explaining why this dang SD card reader is giving me more trouble than patching the broadcom 4318 driver and messing with the xorg.conf and drivers for the ati card COMBINED!**

**[COLOR="Red"]My most sincere apologies for the length and detail of this post, I sure hope the time I spent writing this didn't result in a steamy pile of redundant information. I just wanted to address the common data gathering questions I see requested of those seeking help.[/COLOR]**

---

### Post by macogw on 2007-12-17
2.6.22-14 doesn't need the driver update from my post.  That's just for Feisty, which was released with a broken driver.  It's possible my script downgraded what's in Gutsy by default.  It backs up what was there, though, and there's an uninstall script, so I suggest using that to undo the change my script makes.

---

### Post by Blue_Horseshoe on 2007-12-17
Any idea why I'm having issue with the card reader on this fresh install? I've literally done nothing to it aside from the initial security update and non-free media package. :confused:

---


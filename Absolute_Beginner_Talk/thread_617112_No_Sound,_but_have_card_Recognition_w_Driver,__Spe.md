---
title: "No Sound, but have card Recognition w/ Driver,  Specs included"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Paradoxfox93 on 2007-11-19
Recertified: Gateway MT3422 AMD Mobile Athlon 64 X2 TK-53(1.70GHz) 14.1" Wide XGA 1GB 160GB DVD Super Multi NVIDIA GeForce Go 6100 NoteBook 

[http://www.newegg.com/Product/Product.asp?Item=N82E16834101093](http://www.newegg.com/Product/Product.asp?Item=N82E16834101093)
--------------------------
cat /proc/asound/cards

Returns:
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xb0000000 irq 19
-----------------------------
aplay -l

Returns:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
---------------------------

 asoundconf list
 
 Returns:
Names of available sound cards:
NVidia


lspci

Returns:

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


Symptoms:

At first I Put Gusty on.  Due to crashing trying to set up networking I put feisty on. I still wasn't able to get wireless working so I tried dapper drake.  I also put Vista on just to test my hardware.  I'm back in feisty with KDE installed as well.  I've gotten no sound whatsoever on any of them except Vista (Which is inconceivable as a permanent solution...even if wireless works there too).  I haven't tried to mess with anything in any of the others,  I just observed that I wasn't getting any sound.  There are no settings in the bios reated to sound.   Alsa is not muted and volume is %100.  Basically, I SHOULD be getting sound...but I'm not.  Anyone have a diagnosis and/or solution?

Also, I originally was doing 64 bit, I heard wireless works in 32 bit. So now I have 32 bit feisty.

---

### Post by Paradoxfox93 on 2007-11-19
Okay, so after a bit of digging I found a post with something resembling a solution. Then somebody dissing that guys solution sayin' he's dissin' Ubuntu...

IDK...but the guy claims to have gotten sound working on mt3421 and since i have a mt3422 I'd really like to try his process.  IDC about the polotics, if it works...

Problem is that they are instructions for fedora.  Can someone translate the code for me to use on ubuntu?  It's a little confusing since I know I can't use root to create folders and such and then do what they're saying to do.  I'm quite green so I'd like to try this process as the rest of the thread scares me that I'll be forced to have a deaf&dumb laptop or use vista (Just about equally scary options).  Translation please???

[http://forums.fedoraforum.org/showthread.php?p=868053](http://forums.fedoraforum.org/showthread.php?p=868053)

And the original thread discussing the sound problems for this chipset:

[http://ubuntuforums.org/showthread.php?t=239995&highlight=Gateway+MT3422&page=12](http://ubuntuforums.org/showthread.php?t=239995&highlight=Gateway+MT3422&page=12)

---

### Post by Paradoxfox93 on 2007-11-19
bump, anyone this morning? Please!?

I did update Alsa

---


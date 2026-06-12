---
title: "Help installing a Huion tablet"
date: 2013-07-07
forum: Art &amp; Design
---

### Post by AnUnearthlyChild on 2013-07-07
Huion model 580, the disc it came with installs for windows and apple, is there a way to set up the tablet on linux?

here are the diagnostics: 
```
Bus 001 Device 004: ID 18e3:9102 Fitipower Integrated Technology Inc Multi Card ReaderBus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 005: ID 256c:006e  
Bus 004 Device 002: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
guscoth@HAL-2000:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=10    [slave  pointer  (2)]
&#9116;   &#8627; HUION 580                                   id=13    [slave  pointer  (2)]
&#9116;   &#8627; HUION 580                                   id=14    [slave  pointer  (2)]
&#9116;   &#8627; HUION 580                                   id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=8    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=11    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=12    [slave  keyboard (3)]
guscoth@HAL-2000:~$ 



```

---

### Post by sanderj on 2013-07-07
Did you check
[https://bugs.launchpad.net/wizardpen/+bug/1029951](https://bugs.launchpad.net/wizardpen/+bug/1029951)
[http://ubuntuforums.org/showthread.php?t=2129928](http://ubuntuforums.org/showthread.php?t=2129928)

(Disclaimer: I haven't got a Huion graphic tablet)

---

### Post by gordintoronto on 2013-07-07
I couldn't find any good news. According to this:
[http://sourceforge.net/apps/mediawiki/digimend/?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/?title=Tablet_support_status)

the tablet will be supported in the 3.11 kernel -- which is expected later this year, possibly quite soon. However, that might mean it's in Ubuntu 14.04.

Source code for the driver might be available soon, and that's not as scary as it sounds.

---

### Post by steve5139 on 2014-02-19
I have the 3.11 kernel (Mint 16 on a Dell D620) and tried the Huion H610 without the wizardpen driver. The kernel invokes the evdev driver for it with disasterous results. The tablet is unusable. Back to wizardpen. Best I could do with this tablet is described (at length) in my post here: [http://ubuntuforums.org/showthread.php?t=2205984](http://ubuntuforums.org/showthread.php?t=2205984) - To summarise, with wizardpen, the H610 basically works okay as virtual blackboard, but there's no pressure sensitivity and cannot get the buttons other than the tip don't work properly. Good enough for what I need, but would be nice to have it working properly and being able to do real graphics stuff with it.

---


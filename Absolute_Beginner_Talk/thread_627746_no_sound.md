---
title: "no sound"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by candra on 2007-11-30
Greetings, 

I am a relatively new user of Ubuntu 7.04 Feisty Fawn and I have no sound with this operating system. My volume controls are on high, but I cannot hear anything-- Neither from the Web nor from my cd drive. 

Any help will be greatly appreciated, 

Candra

---

### Post by wolfen69 on 2007-11-30
from the terminal, post the output of:
```
lspci
```

---

### Post by candra on 2007-11-30
Here below is the information that came up. Waiting your reply. Thank you... candra


krpa@Baba-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
krpa@Baba-desktop:~$

---

### Post by Pumalite on 2007-11-30
'00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)'

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Therion on 2007-11-30
I'd suggest starting here:  [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide").

---

### Post by Pumalite on 2007-11-30
Read this also:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by quandary on 2007-11-30
Right click on the sound icon and select preferences.

If there is more than one sound device, try using the other one.
I have to:
HDA Intel (Alsa mixer)
and
SigmaTel 

I normally use alsa, but on some games i have to use sigmatel to get sound.
You can also try to swich the channel from master to PCM or to digital.

Maybe that helps

---

### Post by DutyDuty on 2007-11-30
If your computer is Toshiba make, check the link in my sig. If not, I've got nothing.

---


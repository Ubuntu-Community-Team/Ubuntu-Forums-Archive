---
title: "sound card not working"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by CloudFX on 2008-03-06
Hi, I recently install Ubuntu, and I'm sure that before, my sound was working. I never used it at first, but now, when I try to change it, I get an error message telling me that there is no sound card. What can I do? 

Dual booting Vista/Ubuntu 7.10 (vista sound works)
AMD 64-bit

---

### Post by FuturePilot on 2008-03-06
Can you post the output of
```
lspci
```
so we can see what sound card you have?

---

### Post by CloudFX on 2008-03-06
Thanks for helping!

```
nick@NickPC:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

---

### Post by ferdostar on 2008-03-06
Can you take a look at alsamixer if everything is ok (mean on)?
```
alsamixer
```

EDIT:
If the answer is yes open a terminal and type
```
sudo apt-get install linux-backports-modules-generic
```

reboot and post if there is any changes

---

### Post by CloudFX on 2008-03-06
```
nick@NickPC:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
```

what does that mean?

---

### Post by ferdostar on 2008-03-06
Can you post the output of 
```
aplay -l
```

---

### Post by CloudFX on 2008-03-06
```
nick@NickPC:~$ aplay -l
aplay: device_list:204: no soundcards found...
```

---

### Post by kaginken on 2008-03-06
Since you're dual booting vista - check that you didn't mute the sound in vista.  That will do it.

---

### Post by CloudFX on 2008-03-06
AH, that might be the problem. I'll check on that ASAP. Will I still be able to change the volume using the buttons on my laptop, or will I need to use the Volume Meter?

---

### Post by CloudFX on 2008-03-07
I tried that, to no success. What next?

---

### Post by kaginken on 2008-03-08
Hmmm - I was just troubleshooting similiar problem with mine.  Try :

[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

Also - does it work if running ubuntu from the live cd?  What version of Ubuntu are you using?

---

### Post by CloudFX on 2008-03-08
I'm using Gutsy 64bit.. it also doesn't work on the LiveCD. But I have discovered, that sound does work when I use USB Headphones. I have no issue with this, and we can assume that the problem has been solved! Thanks for your help:KS

---

### Post by nbayiha on 2008-03-09
CloudX can u post please post which model of sound card u have ?

try this command on the terminal

```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by CloudFX on 2008-03-09
I'm unsure what the model is. How can I find this out?

And heres the output...
```

nick@NickPC:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
```

---

### Post by handy on 2008-03-09
This link should sort you out:

***_[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)_***

---

### Post by nbayiha on 2008-03-10
The last link did solve ur problem??
If not, can u post 
```
aplay -l
```

---

### Post by moodog on 2008-03-10
I too have this problem. I didn't manually install any updates, but for some reason on a reboot, /dev/dsp disappeared, and I didn't have any sound. i get this error from alsamixer:

alsamixer: function snd_ctl_open failed for default: No such device

any tips? I've tried installing the linux-generic backports package but it made no difference

mythtv@spankytv:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****

---

### Post by nbayiha on 2008-03-10
moodog post what show of in the terminal when u enter this command

```
cat /proc/asound/card0/codec#* | grep Codec
``` 
and this one
```
aplay -l
```

---

### Post by moodog on 2008-03-10
I only have:

/proc/asound/card1

and it only contains 

id  
midi0  
and oss_mixer


also, the output of aplay -l is as above and below:

mythtv@spankytv:/proc/asound/card1$ aplay -l
**** List of PLAYBACK Hardware Devices ****


also note i'm not running hardy, just normal 7.10

---

### Post by nbayiha on 2008-03-10
when i write aplay -l in the terminal i recieve something like this 

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

but your output is a kind of strange u just posted 
 ```
**** List of PLAYBACK Hardware Devices ****
```
where is the rest ??:confused:
let's assume nothing was written instead of that :)
can u tell me which model of motherboard u are using , and maybe which sound card ur system is having, Maybe a decription of ur system 

mine for example is 
> Codec: Realtek ALC885

You should find yours with the command i gave u 

but like u said there is not codec in that folder please post me the > cat of id i mean > cat /proc/asound/card0/id 

---

### Post by moodog on 2008-03-10
Dammit. Now I think about it I've had this problem before. I basically followed steps under

 Getting the ALSA drivers from a *fresh* kernel

on this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

and it solved the problem.

thanks for help.

---


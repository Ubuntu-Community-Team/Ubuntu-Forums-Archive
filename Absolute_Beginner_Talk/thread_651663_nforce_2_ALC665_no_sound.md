---
title: "nforce 2 ALC665 no sound"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Tango_Down on 2007-12-27
So, I have been without sound for quite a while(Ever since install back in August), My soundcard is detected in Linux, and functioning properly in Windows. There are several post of people with this setup having problems, but no concrete fixes. I have followed the comprehensive sound guide to the best of my ability up to and including recompiling the intel 8x0 drivers. My last attempted fix involved uninstalling alsa and just trying it with OSS. This did not work. Everything is detected fine, but sound is not forthcoming, I have fiddeled with mixer settings for quite a while, and tried to get sound as root, also did not work. I recently upgraded to 7.10 from 7.40, but that did not solve the issue. Also, I have different nforce2 board in a different computer, and it has the same issue with Kubuntu installed on it. Should I collect data and file a bug report? 

Here is a link to a thread of some people with the same issue. 
[http://ubuntuforums.org/showthread.php?t=244018](http://ubuntuforums.org/showthread.php?t=244018)

---

### Post by Tango_Down on 2007-12-27
My ossinfo lines

Version info: OSS 4.0 (b1011/200712200355) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (WeavLNX)

Number of audio devices:        4
Number of audio engines:        21
Number of mixer devices:        2


Device objects
 0: osscore0 OSS core services
 1: ich0 Nvidia nForce2 interrupts=2925 (2991)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support
 4: usb046d0a01-0 Logitec USB Headset
 5: usb046d0a01-1 Logitec USB Headset
 6: usb046d0a01-2 Logitec USB Headset


Mixer devices
ICH AC97 Mixer (ALC655) (Mixer 0 of device object 1)
Logitec USB Headset (Mixer 0 of device object 4)

Audio devices
Nvidia nForce2                    /dev/oss/ich0/pcm0  (device index 0)
Nvidia nForce2 S/PDIF out         /dev/oss/ich0/spdout  (device index 1)
Logitec USB Headset play          /dev/oss/usb046d0a01-1/pcm0  (device index 2)
Logitec USB Headset rec           /dev/oss/usb046d0a01-2/pcmin0  (device index 3)


My lspci lines


00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 USB Controller: NEC Corporation USB (rev 43)
01:07.1 USB Controller: NEC Corporation USB (rev 43)
01:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)


Little help? I know that nforce 2 is a really common board, and it is a fairly big bummer to have no sound.

---

### Post by mattman on 2007-12-27
I have this problem also. I tried many different methods to fix this problem including installing pulseaudio (which was an absolute nightmare to tr and configure). Fortunately I had an old pci sound card laying around that works just fine. I wouldn't mind getting my onboard nforce2 sound working though.

Ron Paul '08

---

### Post by Tango_Down on 2007-12-27
I suppose I could go to the local shop and buy a 5 dollar PCI soundcard from the "Maybe it works?" bin, but that seems like a pretty duct-tapey fix, and it costs money for something I already shelled out good cash for. (Have any idea how hard it is to find a good socket A board these days?):) Anyway, this seems like one of those issues that gets stuck by the wayside as people move on to biggger and better hardware, this is my second or third post on the issue. The PCI sound card might be the only way.

---

### Post by mattman on 2007-12-28
> = (Have any idea how hard it is to find a good socket A board these days?).

I had to replace mine less than a month ago and ended up getting a refurbed Epox board directly from them. The funny thing is that my old board which was also an nforce2 Epox had onboard sound working great. The pci sound card is just a  temporary measure for me, I assume that at some point this issue will be resolved.

---


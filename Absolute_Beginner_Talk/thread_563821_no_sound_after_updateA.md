---
title: "no sound after updateA"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by docfl on 2007-09-30
After recent updates, I can no longer hear sounds. I am dual boot with vista and have sounds with that. I did some searching and I see Ubuntu is showing a sound card. I found help at:[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)
titled Ubuntu no sound troubleshooting, and followed instructions. I should mention that I know enough about comptuers to get into trouble with them. :confused:
This is what I get when I type in lspci:
don@don-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
don@don-laptop:~$ 
 
Then I put in :

don@don-laptop:~$ sudo totem
Password:

** (totem:6301): WARNING **: Failed to connect to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (totem:6301): WARNING **: Error connecting to DBus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
don@don-laptop:~$

---

### Post by Pumalite on 2007-09-30
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by docfl on 2007-09-30
Ok I went to that page as well. It shows the following: don@don-laptop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 18
don@don-laptop:~$ 

and under user privilege it shows I have sound listed as ok.
Thanks anyway

---

### Post by docfl on 2007-10-02
Some more info.

don@don-laptop:~$ cat /proc/asound/cards
0 [SB ]: HDA-Intel - HDA ATI SB
HDA ATI SB at 0xc0000000 irq 18
don@don-laptop:~$
when I put in the command to show the devices, it shows this:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0

I had it working when I first installed Ubuntu then when I ran updates, it quit working.
Thanks for the assist.
docfl

---


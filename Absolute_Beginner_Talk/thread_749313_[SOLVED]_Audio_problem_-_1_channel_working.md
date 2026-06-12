---
title: "[SOLVED] Audio problem - 1 channel working"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by phannigan on 2008-04-08
Recently installed 7.10 Ubuntu and I am having audio problems. Using ASUS MB (A8V-VM) with onboard audio but only 1 channel works and volume is extremely low. I have searched the forum for answers but have not been able solve. Any suggestions for this NuBee? Thanks.

---

### Post by herbster on 2008-04-08
Open a terminal and paste the output of this command:

```
lspci
```

Use [code] tags please.

---

### Post by phannigan on 2008-04-08
paul@paul-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce PCX 5750] (rev a2)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller
paul@paul-desktop:~$

---

### Post by herbster on 2008-04-08
Okay, have you checked the mixer levels? Hit ALT+F2 and type "gnome-volume-manager" and hit ENTER. What are the mixer levels? All the way up and unmuted?

---

### Post by phannigan on 2008-04-08
> **herbster said:**
> Okay, have you checked the mixer levels? Hit ALT+F2 and type "gnome-volume-manager" and hit ENTER. What are the mixer levels? All the way up and unmuted?

Thanks Herbster - ALT+F2 does not do anything.

---

### Post by herbster on 2008-04-08
Okay, are you using Gnome? Do you see a little volume icon in the corner of your menubar? Right-click that and hit the option for editing the levels, it's Preferences or something, I can't recall exactly.

---

### Post by phannigan on 2008-04-08
All levels seem to be OK. i wanted to put a screenshot in this reply but not sure how to do it either! Thanks for your continued help.

---

### Post by herbster on 2008-04-08
Okay, go back to a terminal and try this (hit CTRL+C to cancel after you have some output, whether you hear sound or what errors it gives you so you can paste back here, as it will run indefinitely unless you CTRL+C at some point):

```
speaker-test -c2 -twav -Ddefault
```

---

### Post by phannigan on 2008-04-08
Here's the response:
paul@paul-desktop:~$ speaker-test -c2 -twav -Ddefault

speaker-test 1.0.14

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 2.688868
 0 - Front Left
 1 - Front Right
Time per period = 3.007910
 0 - Front Left
 1 - Front Right
Time per period = 3.007913
 0 - Front Left
 1 - Front Right

---

### Post by herbster on 2008-04-08
Right, but do you hear the voice saying "front left" and "front right" ??

---

### Post by phannigan on 2008-04-08
I get "Front - Right" voice only. Left has a high pitched whistle from it. Front Right volume is low as well.

---

### Post by phannigan on 2008-04-08
As an aside, here is a screenshot when I use "alsamixer" in Terminal.

---

### Post by dkdwong on 2008-04-10
I had the exact same problem with ASUS M2A-VM motherboard with on board Realtek ALC883.

In my case I upgraded to Hardy Heron.  The Alsa mixer has option of 2, 4, or 6 speaker system.

In the 6 speaker system mode the mike jack becomes the rear speaker, the line in jack becomes the center speaker.  This is what suppose to happen.  In my case the mic jack works left and right, the front speak jack stayed as the right channel only, and the line in jack becomes the left channel only.

This is sort of a work around.  Still trying to fix the problem correctly as this does not work the same in Windows.

---

### Post by phannigan on 2008-04-10
> **dkdwong said:**
> I had the exact same problem with ASUS M2A-VM motherboard with on board Realtek ALC883.

In my case I upgraded to Hardy Heron.  The Alsa mixer has option of 2, 4, or 6 speaker system.

In the 6 speaker system mode the mike jack becomes the rear speaker, the line in jack becomes the center speaker.  This is what suppose to happen.  In my case the mic jack works left and right, the front speak jack stayed as the right channel only, and the line in jack becomes the left channel only.

This is sort of a work around.  Still trying to fix the problem correctly as this does not work the same in Windows.

Thanks very much. I will try the upgrade and see! I'll post my findings as well - hoping it will help others with similar situation. I was going to order a PCI sound card to see if that solves the problem as well. Best regards.:)

---

### Post by phannigan on 2008-04-10
Upgraded to Hardy Heron and problem is resolved!
Thanks to all for their input!

---

### Post by herbster on 2008-04-10
This is most likely a result of updated alsa/drivers that come with Hardy a default. Glad it's solved, phannigan, can you go Thread Tools > Mark as Solved for others? Thanks :)

---

### Post by jeffemmert on 2008-04-13
It works when I boot in XP, but not in Ubuntu 7.10 - left channel only using test tones, mp3s, startup & shutdown sounds.

Results of test:

lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:02.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)

02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)

02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

I've seen many similar posts of this left channel only thing. Could it be an o/s bug?

---

### Post by herbster on 2008-04-14
Have you checked your mixer levels and that all are up and unmuted? Have you run speaker-test as I posted earlier in this thread and can you paste the output?

---


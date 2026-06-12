---
title: "No Sound in Dapper"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Otto-C on 2007-01-07
I get no sound in Dapper. 
Tried the following:
Amarok in the Playlist gives message
Xine unable to initialize drivers.
Audacity gives Host Error
Beepmedia Player gives nothing
Kaffeine Tried to open player but gives
Loading Player part failed. All audio drivers failed.
Clicked on Volume Control on desktop panel shows
ERROR basically says you don't have the right GStreamer
plugins installed or no soundcard.

My guess is I have no audio drivers active as there is an 
audio card. See results of #lspci below.

How to load/install audio drivers

#lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by lyceum on 2007-01-07
What kind of sound card do/should you have?

---

### Post by deadgobby on 2007-01-07
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
 That intergrated card should work. Have you see if you may need to unmute "Master Surround" even if you only have two speakers. 
Or see if this link will help.
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
 Is your system a Dell???
Gobby

---

### Post by Otto-C on 2007-01-07
Your right the system is a Dell. Its a laptop Inspiron B130.
alsa is present but when I do alsamixer it gives:
alsamixer: function snd_ctl_open failed for default: Not such device

The laptop is dual boot with pclinuxos and the sound works OK but
I prefer Kubuntu.

Basically I'm a real novice.
My last update was done in late July. I prefer to stay with Dapper.

---

### Post by deadgobby on 2007-01-08
I think you may need to do an update. It has been several months. Any ways
[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspironB130?highlight=%28dell%29](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspironB130?highlight=%28dell%29)
 It looks like the testing fail on dapper, but sound was working in Eft. 
Gobby

---

### Post by azkehmm on 2007-01-08
Yeah... if it's a dell with sorround and stuff, you'll propably need to poke around with the Alsamixer a little. I have to unmute master sorround and anoter tab (of wich I can't remember the name) in order to get sound from my PC (Dell Dimension 4600 with an ICH5), so before poking around with drivers, try the alsamixer thing.

---


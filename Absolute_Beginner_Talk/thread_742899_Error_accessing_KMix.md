---
title: "Error accessing KMix"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by xecure on 2008-04-02
Hi there,
i was running KAlarm and wanted to set an alarm with an audio sound, I also set the option to set the master volume to high. When I clicked on "Try" for the alarm the notification when up correctly but the sound file did not play neither was the sound volume set to high. In fact it gave me an error which said:  > Unable to set master volume
(Error Accessing KMix:
could not find service 'kmix'.)Any ideas on how to fix this?

As a college student kAlarm would do me wonders if this feature worked properly

---

### Post by c-ron on 2008-04-02
From the terminal:
```
sudo apt-get install kmix
```

---

### Post by xecure on 2008-04-02
that solved my KMix error problem, now when I hit 'try' on an event the message just pops up with no sound playing. The volume does get set to high but no sound is played after that.

---

### Post by Crafty Kisses on 2008-04-02
> **xecure said:**
> that solved my KMix error problem, now when I hit 'try' on an event the message just pops up with no sound playing. The volume does get set to high but no sound is played after that.

Hmmm, post the following output:
```
lspci
```

---

### Post by xecure on 2008-04-02
```
lspci
``` outputs:
```
zaki@zaki-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

---

### Post by c-ron on 2008-04-02
Load kmix (or alsamixer from the terminal) and make sure nothing (like pcm playback) is muted or turned all the way down.
In alsamixer, left & right arrow keys select the control, up & down arrow keys adjust sliders, and the M key toggles Mute/Unmute and also On/Off.

If that doesn't work, try specifying your model of soundcard in /etc/modprobe.d/alsa-base by adding this line to the bottom of the file:
options snd-hda-intel model=3stack 

Reboot and try again. See: [http://ubuntuforums.org/archive/index.php/t-461794.html](http://ubuntuforums.org/archive/index.php/t-461794.html)

---

### Post by xecure on 2008-04-04
everything in alsamixer and KMix is turned up. but sometimes i dont want my volume to be high since i carry around my laptop. I wanted kAlarm to raise my volume right before the alrm went off. After the alrm goes off I can adjust my volume to somethign lower agaig

---

### Post by xecure on 2008-04-05
bump =\

---


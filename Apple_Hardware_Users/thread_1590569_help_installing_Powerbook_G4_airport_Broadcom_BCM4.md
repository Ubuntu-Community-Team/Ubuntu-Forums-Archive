---
title: "help installing Powerbook G4 airport Broadcom BCM43xx IEEE 802.11b wireless"
date: 2010-10-08
forum: Apple Hardware Users
---

### Post by thepotatobasher on 2010-10-08
so I've been struggling trying to get my wireless card to actually connect to my network. Even though my airport detects available networks, it can't connect to any. I know i could just buy a usb dongle and be done with it but i enjoy a challenge and i'm trying to learn to use linux.

I have a powerbook G4.  I'm unsure about the exact wireless driver but i'm pretty sure that I had the original powerbook G4, which has the 802.11b modem, which appears to be supported. 

here are some articles that i dug up. 

[http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy](http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy)
[http://manpages.ubuntu.com/manpages/lucid/man4/bwi.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/bwi.4freebsd.html)

i tried to do lspci and i couldn't find my wireless card among the devices

---

### Post by linuxopjemac on 2010-10-08
output of 
```
lspci -vnn | grep 14e4
```
please

---

### Post by thepotatobasher on 2010-10-08
> **linuxopjemac said:**
> output of 
```
lspci -vnn | grep 14e4
```please

i wasn't able to get any output from that at all. 

here is output from straight lspci

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:24:0e.0 FireWire (IEEE 1394): Agere Systems FW322/323
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)



Oddly enough, i went into Network Tools and there were 3 devices listed:
ethernet interface (eth0)
ethernet interface (eth1)
loopback interface (lo)


Also, using synaptic package manager, i installed
broadcom-sta-common
broadcom-sta-source
b43-fwcutter

---

### Post by thepotatobasher on 2010-10-09
so since there isn't any output of lspci that has anything to do with my wireless does that mean that my wireless isn't a pci device?  what else could it be???

The thing that confuses me more than anything is my wireless is working

It detects networks, but can't connect to them...

---

### Post by camrto on 2011-02-10
Hi there . exactly same problem here. Can see networks but cant connect. i got a powerbook g4 17inches.

Have you solved this issue? I tried the same things you did with no look. will keep an eye on this. cherrs

---

### Post by linuxopjemac on 2011-02-10
I see in the wireless thread
[http://ubuntuforums.org/showthread.php?p=9957641#post9957641](http://ubuntuforums.org/showthread.php?p=9957641#post9957641) 
an orinoco module. That points to a classic Airport instead of Broadcom.
You might want to install linux-firmware-nonfree, that's the package in MintPPC that provides firmware for older airport models. This will give you:

Agere/Prism/Symbol Orinoco firmware (STA mode), version 9.48 Hermes I (agere_sta_fw.bin)


All airport cards work out of the box nowadays in MintPPC...

You also need to have the latest firmware from Apple for this card (9.52).

---

### Post by getphuture on 2012-04-14
How did you do please ? I have an old powerbook G4 Titanium with orinoco, I installed linux-firwmare-nonfree but nothing changed. I still can't connect to my wifi setup with a WEP key
Any idea ?

lsmod:
```

Module                  Size  Used by
binfmt_misc             8530  1 
ppdev                   7877  0 
lp                      9304  0 
radeon                807934  0 
parport                39110  2 ppdev,lp
ttm                    62726  1 radeon
drm_kms_helper         31243  1 radeon
drm                   194088  3 radeon,ttm,drm_kms_helper
apm_emu                 1468  0 
apm_emulation           7311  2 apm_emu
dm_crypt               14921  0 
snd_powermac           68343  1 
snd_pcm_oss            47872  0 
snd_aoa_i2sbus         20791  0 
snd_mixer_oss          19382  1 snd_pcm_oss
snd_seq_dummy           1766  0 
snd_pcm                87159  3 snd_powermac,snd_pcm_oss,snd_aoa_i2sbus
snd_seq_oss            36288  0 
snd_seq_midi            6161  0 
michael_mic             2384  4 
snd_rawmidi            24746  1 snd_seq_midi
ipv6                  301244  16 
snd_seq_midi_event      7367  2 snd_seq_oss,snd_seq_midi
snd_seq                61897  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 37678  0 
airport                 3786  0 
snd_timer              24531  2 snd_pcm,snd_seq
snd_seq_device          7524  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sg                     32495  0 
yenta_socket           25736  1 
orinoco                71915  1 airport
sd_mod                 36596  0 
rsrc_nonstatic         11098  1 yenta_socket
cfg80211              152841  1 orinoco
evdev                  10257  15 
crc_t10dif              1331  1 sd_mod
snd                    70676  12 snd_powermac,snd_pcm_oss,snd_aoa_i2sbus,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtc_generic             1391  0 
sr_mod                 16052  0 
pmac_zilog             18110  0 
serial_core            23813  1 pmac_zilog
sbp2                   22505  0 
pcmcia_core            40156  3 pcmcia,yenta_socket,rsrc_nonstatic
rfkill                 20725  1 cfg80211
snd_aoa_soundbus        4916  1 snd_aoa_i2sbus
soundcore               7534  1 snd
snd_page_alloc          7660  1 snd_pcm
windfarm_core          10420  0 
ohci1394               35584  1 
sungem                 32704  0 
usb_storage            46938  0 
ieee1394               97330  2 sbp2,ohci1394
sungem_phy             12365  1 sungem
uninorth_agp            8437  1 
agpgart                39983  3 ttm,drm,uninorth_agp
```lspci:
```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:24:0e.0 FireWire (IEEE 1394): Agere Systems FW322/323
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)
```

---

### Post by linuxopjemac on 2012-04-14
Try a connection with WPA security. Be sure that you upgrade the firmware in that card to the latest with OS9.

---

### Post by getphuture on 2012-04-15
Thanks linuxopjemac ! ! !. I dug a little bit and found that's older airport can't use WEP.
I connected to my wifi device remotely and switch to WPA key.
Bingo,  everything works now ! ! ! =D>

I removed broadcom-sta-common, broadcom-sta-source, b43-fwcutter, and linux-firmware-nonfree and everything still works ! Not shure if it's needed. The output of lspci and lsmod hasn't changed too. Using ubuntu 10.04 LTS with lxde

Yes !

---

### Post by ktkoma on 2012-07-19
The linux-firmware-nonfree worked and my G4PPC found the wireless and hooked up without any problems.  Thanks

---

### Post by heinzgitz on 2012-11-25
getphuture ich habe das gleiche Probleme, zwar mit der Aria extreme Karte für Wireless.
Und werde es auch so versuchen wie von Dir beschrieben.

Gruss
Heinz Gitz

---

### Post by heinzgitz on 2012-11-25
getphuture ich habe das gleiche Probleme, zwar mit der Aria extreme Karte für Wireless.
Und werde es auch so versuchen wie von Dir beschrieben.

Gruss
Heinz Gitz

---


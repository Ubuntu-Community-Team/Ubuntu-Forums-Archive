---
title: "PowerBook G4 Aluminum Ubuntu 9.10 issues"
date: 2010-04-26
forum: Apple Hardware Users
---

### Post by Dukenukemx on 2010-04-26
Decided to switch my aging PowerBook G4 to Ubuntu.  This was because support for PPC on Mac was dead.  I installed Ubuntu 9.10 and it's running good so far, but there are some issues I have that I'm hoping others here can help with.

#1  No battery meter.  I actually fixed this by adding pmu_battery to /etc/modules.  

#2  Wifi doesn't work after it sleeps.  It will work once I restart it, but that's annoying.  

#3  Gnash doesn't do anything.  Yes I want flash working, but Gnash just produces white boxes where flash should be.  

#4  XBMC won't install.  Just keeps saying required crap and refuses to install.  

If anyone can help me with these problems, it would be great.

---

### Post by linuxopjemac on 2010-04-26
Which module is repsonsible for wireless ? is it orinoco ?

give me the output of

```
sudo lsmod
```

---

### Post by Dukenukemx on 2010-04-26
Module                  Size  Used by
binfmt_misc             9800  1 
ppdev                   8848  0 
lp                     10684  0 
parport                40108  2 ppdev,lp
ipv6                  299236  10 
radeon                382344  2 
drm                   177704  3 radeon
rfcomm                 45084  4 
sco                    12064  2 
pmu_battery             2540  0 
therm_adt746x          10700  0 
apm_emu                 2004  0 
apm_emulation           8640  2 apm_emu
snd_powermac           65276  0 
bridge                 57296  0 
snd_aoa_codec_tas      12708  2 
stp                     2748  1 bridge
snd_pcm_oss            48484  0 
snd_aoa_fabric_layout    12516  2 
bnep                   14596  2 
snd_mixer_oss          20240  1 snd_pcm_oss
snd_aoa                17768  2 snd_aoa_codec_tas,snd_aoa_fabric_layout
snd_aoa_i2sbus         21368  1 
snd_pcm                86464  3 snd_powermac,snd_pcm_oss,snd_aoa_i2sbus
pcmcia                 39428  0 
snd_seq_dummy           2880  0 
iptable_filter          3276  0 
arc4                    1664  2 
snd_seq_oss            36156  0 
l2cap                  25824  16 rfcomm,bnep
ip_tables              14588  1 iptable_filter
snd_seq_midi            7756  0 
ecb                     3064  2 
snd_rawmidi            26312  1 snd_seq_midi
snd_seq_midi_event      7296  2 snd_seq_oss,snd_seq_midi
yenta_socket           28204  1 
snd_seq                60732  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25628  2 snd_pcm,snd_seq
rsrc_nonstatic         11972  1 yenta_socket
snd_seq_device          8236  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   141816  0 
pcmcia_core            41624  3 pcmcia,yenta_socket,rsrc_nonstatic
x_tables               19132  1 ip_tables
snd                    71740  17 snd_powermac,snd_aoa_codec_tas,snd_pcm_oss,snd_aoa_fabric_layout,snd_mixer_oss,snd_aoa,snd_aoa_i2sbus,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              203308  1 b43
btusb                  13444  2 
soundcore               7396  1 snd
cfg80211              106844  2 b43,mac80211
bluetooth              64560  9 rfcomm,sco,bnep,l2cap,btusb
pmac_zilog             18648  0 
snd_aoa_soundbus        5596  2 snd_aoa_fabric_layout,snd_aoa_i2sbus
serial_core            24972  1 pmac_zilog
rfkill                 21616  4 cfg80211,bluetooth
evdev                  11864  14 
rtc_generic             1948  0 
snd_page_alloc         10292  1 snd_pcm
windfarm_core          11456  0 
sungem                 33340  0 
sungem_phy             11832  1 sungem
ohci1394               36928  0 
ieee1394               96900  1 ohci1394
ssb                    42348  1 b43
uninorth_agp            9516  1 
agpgart                40860  2 drm,uninorth_agp

---

### Post by linuxopjemac on 2010-04-26
ok, you use b43, sounds logically. I guess if you jsut remove b43 and reload after sleep, you would have wireless again, so after sleep:
```

sudo rmmod -f b43
sudo modprobe b43
```

if that works you can add a file /etc/pm/config.d/local-sleep-modules, containing the line:

```
SUSPEND_MODULES="b43"
```

---

### Post by linuxopjemac on 2010-04-26
on my MacBook I did it like this:
[http://ubuntuforums.org/showthread.php?t=1432207](http://ubuntuforums.org/showthread.php?t=1432207)

---

### Post by Dukenukemx on 2010-04-26
Thanks linuxopjemac, I put SUSPEND_MODULES="b43" into my 00sleep_module and my wifi is still going.  That saved me a lot of aggravation.  

Does anyone have flash working at all on ppc linux?  I heard the newest Google Chrome web browser has integrated flash support.  Does Chrome work on ppc linux?

Lastly, I still can't get XBMC to install.  Is there an alternative media center for Ubuntu?  I use MediaPortal on a windows machine that has a capture card, so I can watch TV from it through streaming.

---


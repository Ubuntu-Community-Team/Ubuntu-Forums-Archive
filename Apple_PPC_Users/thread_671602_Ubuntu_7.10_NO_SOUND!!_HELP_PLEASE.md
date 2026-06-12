---
title: "Ubuntu 7.10 NO SOUND!! HELP PLEASE"
date: 2008-01-18
forum: Apple PPC Users
---

### Post by Dr.Greenmac on 2008-01-18
Hey partners...
I have allready installed Ubuntu 7.10 with alternate install cd con mi ibook G4
Everything seems to be wotking just fine exept for the fact that i have NO AUDIO, when i press the audio image on the top right corner it tels me ¨No volume control GStreamer plugins and/or devices found.¨.
Ive been researching but i dont find out whats going on, I allready installed ALL the gstreamer plugins from Synaptic.
In case this helps this ate some outputs i got from the terminal with these comands:

administrador@ubuntu:~$ [COLOR="Navy"]**lspci**[/COLOR]
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)


administrador@ubuntu:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)


administrador@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  313988  8 
af_packet              26056  2 
usbhid                 32372  0 
hid                    36000  1 usbhid
radeon                146152  2 
drm                    99128  3 radeon
rfcomm                 47228  2 
l2cap                  26340  11 rfcomm
bluetooth              66412  4 rfcomm,l2cap
uinput                 11264  2 
ppdev                  11300  0 
lp                     13580  0 
parport                44624  2 ppdev,lp
cpufreq_stats           6372  0 
cpufreq_conservative     8224  0 
cpufreq_userspace       5364  1 
cpufreq_powersave       2048  0 
cpufreq_ondemand        9600  0 
therm_adt746x          13612  0 
sbp2                   25416  0 
scsi_mod              186316  1 sbp2
loop                   22180  0 
apm_emu                 2464  0 
apm_emulation           9980  2 apm_emu
snd_aoa_i2sbus         25060  0 
snd_pcm_oss            54560  0 
snd_mixer_oss          20896  1 snd_pcm_oss
snd_pcm                96548  2 snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         12104  1 snd_pcm
snd_seq_dummy           4036  0 
snd_seq_oss            40820  0 
snd_seq_midi           10016  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      8192  2 snd_seq_oss,snd_seq_midi
snd_seq                62464  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26692  2 snd_pcm,snd_seq
snd_seq_device          9452  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70004  9 snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8996  1 snd
snd_aoa_soundbus        7780  1 snd_aoa_i2sbus
pmac_zilog             21444  0 
serial_core            24768  1 pmac_zilog
bcm43xx               143796  0 
ieee80211softmac       35040  1 bcm43xx
ieee80211              36709  2 bcm43xx,ieee80211softmac
ieee80211_crypt         6592  1 ieee80211
uninorth_agp           12012  1 
agpgart                41340  2 drm,uninorth_agp
evdev                  12736  17 
ext3                  159624  1 
jbd                    68808  1 ext3
mbcache                 9572  1 ext3
ide_cd                 36996  0 
cdrom                  48252  1 ide_cd
ide_disk               21312  3 
sungem                 36260  0 
sungem_phy             13152  1 sungem
ohci1394               43312  0 
ieee1394              111296  2 sbp2,ohci1394
ide_core              172784  2 ide_cd,ide_disk
ehci_hcd               40620  0 
ohci_hcd               36452  0 
usbcore               164116  4 usbhid,ehci_hcd,ohci_hcd
windfarm_core          14544  0 
fuse                   53332  1 
apparmor               48868  0 
commoncap               7968  1 apparmor

Please help me, cause i work a lot with sound and video, and without it, my only option will be going back to OS X. :(

Thanks

---

### Post by flamelab on 2008-01-18
Go here -->[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/]("http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/")

Before that , try putting in terminal

```
alsaconf 
```

---

### Post by frog_pilot on 2008-01-19
add the line

```
snd-powermac
```

to your /etc/modules/, restart your system and everything will work fine.

---


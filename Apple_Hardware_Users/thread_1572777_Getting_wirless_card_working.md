---
title: "Getting wirless card working"
date: 2010-09-11
forum: Apple Hardware Users
---

### Post by Tystick86 on 2010-09-11
Hello everyone,

This is my first post. I recently installed Ubuntu on my PowerPC G4 mac. The either net works fine but the wireless does not.

There is no connections listed under the network connections.

The output of sudo lsmod is
tyrel@tr-ubuntu:~$ sudo lsmod
Module                  Size  Used by
nls_utf8                1397  0 
isofs                  35744  0 
binfmt_misc             8530  1 
rfcomm                 43733  4 
ppdev                   7877  0 
lp                      9304  0 
parport                39110  2 ppdev,lp
sco                    10661  2 
bridge                 57998  0 
stp                     2244  1 bridge
bnep                   12779  2 
l2cap                  37132  16 rfcomm,bnep
radeon                803118  0 
ttm                    62566  1 radeon
drm_kms_helper         31243  1 radeon
uinput                  8693  2 
drm                   192366  3 radeon,ttm,drm_kms_helper
ipv6                  299918  10 
snd_aoa_codec_tas      12436  2 
snd_aoa_fabric_layout    10954  2 
snd_aoa                17240  2 snd_aoa_codec_tas,snd_aoa_fabric_layout
snd_aoa_i2sbus         20791  1 
snd_powermac           68187  0 
snd_pcm_oss            47872  0 
snd_mixer_oss          19382  1 snd_pcm_oss
snd_pcm                87095  3 snd_aoa_i2sbus,snd_powermac,snd_pcm_oss
snd_seq_dummy           1766  0 
snd_seq_oss            36232  0 
snd_seq_midi            6161  0 
snd_rawmidi            24746  1 snd_seq_midi
snd_seq_midi_event      7367  2 snd_seq_oss,snd_seq_midi
arc4                    1345  2 
snd_seq                61897  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ecb                     2495  2 
pcmcia                 37678  0 
snd_timer              24515  2 snd_pcm,snd_seq
snd_seq_device          7524  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   196686  0 
btusb                  13383  2 
bluetooth              64147  9 rfcomm,sco,bnep,l2cap,btusb
snd                    70628  17 snd_aoa_codec_tas,snd_aoa_fabric_layout,snd_aoa,snd_aoa_i2sbus,snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 11669  0 
yenta_socket           25736  1 
mac80211              243467  1 b43
snd_page_alloc          7660  1 snd_pcm
ams                     9413  0 
soundcore               7534  1 snd
rsrc_nonstatic         11098  1 yenta_socket
cfg80211              152734  2 b43,mac80211
evdev                  10257  24 
input_polldev           3402  1 ams
rtc_generic             1391  0 
appletouch              9973  0 
pmac_zilog             18110  0 
snd_aoa_soundbus        4916  2 snd_aoa_fabric_layout,snd_aoa_i2sbus
serial_core            23813  1 pmac_zilog
uninorth_agp            8437  1 
pcmcia_core            40156  3 pcmcia,yenta_socket,rsrc_nonstatic
rfkill                 20725  4 bluetooth,cfg80211
agpgart                39895  3 ttm,drm,uninorth_agp
loop                   16948  0 
apm_emu                 1468  0 
apm_emulation           7311  2 apm_emu
hid_apple               5532  0 
usbhid                 44238  0 
hid                    78460  2 hid_apple,usbhid
ohci1394               35584  0 
ssb                    50495  1 b43
sungem                 32704  0 
sungem_phy             12365  1 sungem
ieee1394               97330  1 ohci1394
mmc_core               69051  1 ssb
windfarm_core          10420  0 

If any one can help I would greatly appreciate it.

---

### Post by linuxopjemac on 2010-09-12
Be sure to be connected to the internet with your wired conenction. Then do:

```
sudo apt-get install b43-fwcutter
```

Let it do its job.

---


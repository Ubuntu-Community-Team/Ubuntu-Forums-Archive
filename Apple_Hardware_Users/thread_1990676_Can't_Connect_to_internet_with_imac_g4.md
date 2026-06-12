---
title: "Can't Connect to internet with imac g4"
date: 2012-05-29
forum: Apple Hardware Users
---

### Post by L1313 on 2012-05-29
I recently received an imac g4 (800MHz 256mb ram ilamp) as a gift. It had tiger on it. It didn't have an airport card so I used my ralink n3 as a wireless adapter. After installing the drivers from the included cd it worked great. After that I decided to try and install ubuntu 8.04 onto it. I got rid of tiger and did a clean install. I'm very new to ubuntu (and linux in general) and couldn't figure out how to install the needed drivers for my n3 to work in 8.04. I read somewhere that the n3 was plug and play with 9.04 so decided to upgrade. After the upgrade i still can't get it to connect to the internet. i thought about downloading updates via an ethernet connection but that didn't work. 

How can I connect the computer to the internet?

Any help you can give me would be appreciated!

---

### Post by llamabr on 2012-05-30
It would help to know the particular chipset of your usb device.  Post the output of:

```
lsusb
```

---

### Post by L1313 on 2012-05-30
This is what I got:


```
lucas@ubuntu:~$ lsusb
Bus 002 Device 004: ID 05ac:0306 Apple, Inc. Optical USB Mouse [Fujitsu]
Bus 002 Device 003: ID 05ac:0204 Apple, Inc. 
Bus 002 Device 002: ID 05ac:1002 Apple, Inc. Extended Keyboard Hub [Mitsumi]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. 
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lucas@ubuntu:~$
```

---

### Post by llamabr on 2012-05-31
Have a look at:

[http://ubuntuforums.org/showthread.php?t=1653688](http://ubuntuforums.org/showthread.php?t=1653688)

[http://ubuntuforums.org/showthread.php?t=960642&page=24](http://ubuntuforums.org/showthread.php?t=960642&page=24)

It would also help us to see the output of:

```
lsmod
```

before you start messing about, too.

That second thread is a good place to post this sort of problem, btw

---

### Post by L1313 on 2012-05-31
Thanks for all your help! I'll post in the other thread.

Here is the output of ```
lsmod
```:


```
lucas@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3840  1 
nls_cp437               5504  1 
vfat                   12160  1 
fat                    56060  1 vfat
sg                     31668  0 
sd_mod                 28116  2 
usb_storage            83112  1 
ppdev                   8932  0 
lp                      9932  0 
parport                37936  2 ppdev,lp
sco                    10920  2 
bridge                 53540  0 
stp                     2692  1 bridge
bnep                   14048  2 
rfcomm                 40436  0 
l2cap                  22180  6 bnep,rfcomm
bluetooth              59824  6 sco,bnep,rfcomm,l2cap
uinput                  8544  2 
ipv6                  274064  8 
sbp2                   21740  0 
scsi_mod              162808  4 sg,sd_mod,usb_storage,sbp2
loop                   16876  0 
apm_emu                 1984  0 
apm_emulation           8000  2 apm_emu
snd_aoa_i2sbus         20004  0 
snd_pcm_oss            42656  0 
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                75684  2 snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc          9448  1 snd_pcm
snd_seq_dummy           2852  0 
snd_seq_oss            35444  0 
snd_seq_midi            7104  0 
snd_rawmidi            24288  1 snd_seq_midi
snd_seq_midi_event      7136  2 snd_seq_oss,snd_seq_midi
snd_seq                56896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23396  2 snd_pcm,snd_seq
snd_seq_device          7596  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62420  9 snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
evdev                  11076  21 
soundcore               6916  1 snd
pmac_zilog             17828  0 
serial_core            24044  1 pmac_zilog
snd_aoa_soundbus        5540  1 snd_aoa_i2sbus
uninorth_agp            9100  1 
agpgart                38460  1 uninorth_agp
ext3                  143304  1 
jbd                    48340  1 ext3
mbcache                 8096  1 ext3
usbhid                 37556  0 
hid                    45896  1 usbhid
ohci1394               34768  0 
sungem                 32356  0 
sungem_phy             11680  1 sungem
ieee1394               92060  2 sbp2,ohci1394
ide_cd_mod             39272  0 
cdrom                  39672  1 ide_cd_mod
ide_gd_mod             24484  3 
windfarm_core          11248  0 
lucas@ubuntu:~$ 
```

---


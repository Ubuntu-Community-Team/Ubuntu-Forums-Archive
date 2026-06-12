---
title: "G4 with Kino0.8 no capture or import"
date: 2006-03-24
forum: Apple PPC Users
---

### Post by falloutvictim on 2006-03-24
I'm having trouble with Kino.  It won't import my avi files, and it won't capture properly.  DVGrab works fine, and I'm trying a DVGrab capture as raw dv instead of avi to see if that will work with Kino.
When I do try and capture with Kino, (as root, I haven't set up my permissions yet), it tells me the AV/C isn't enabled.  I enable it, click capture, then it starts flashing between 

AV/C not enabled and 
WARNING: raw394 kernel module not loaded or failure to read/write /dev/raw1394!

Now if I click on the edit tab, try to import avi, wait for my error mesasge and then go back to the capture tab, I can enable AV/C and try the capture again.

lsmod shows this:

Module                  Size  Used by
binfmt_misc            13864  1
rfcomm                 45852  0
l2cap                  28356  5 rfcomm
bluetooth              60712  4 rfcomm,l2cap
cpufreq_userspace       5356  0
cpufreq_stats           6468  0
cpufreq_powersave       1888  0
cpufreq_ondemand        7580  0
cpufreq_conservative     8868  0
r128                   53828  1
drm                    80440  2 r128
ipv6                  300456  14
af_packet              20840  2
tsdev                   9120  0
ide_floppy             22688  0
usblp                  15072  0
uninorth_agp           10952  1
agpgart                38876  2 drm,uninorth_agp
dm_mod                 67124  1
dv1394                 23084  0
evdev                  11936  4
raw1394                32824  4
ohci1394               40436  1 dv1394
sr_mod                 20964  0
snd_powermac           53700  0
snd_pcm_oss            65024  0
snd_mixer_oss          22048  1 snd_pcm_oss
snd_pcm               106020  2 snd_powermac,snd_pcm_oss
snd_timer              28388  1 snd_pcm
snd                    63668  5 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11364  1 snd
snd_page_alloc         11880  1 snd_pcm
sbp2                   26024  0
scsi_mod              171488  2 sr_mod,sbp2
ieee1394              434320  4 dv1394,raw1394,ohci1394,sbp2
apm_emu                 7916  1
md                     53588  0
ext3                  143272  1
jbd                    70456  1 ext3
mbcache                11076  1 ext3
usbhid                 55556  0
sungem                 37220  0
sungem_phy              9728  1 sungem
ohci_hcd               25188  0
usbcore               137972  4 usblp,usbhid,ohci_hcd
ide_cd                 48548  0
cdrom                  47420  2 sr_mod,ide_cd
ide_disk               20544  3
unix                   31124  48

This is Kino 0.8 that I compiled from tar.gz.

Is there something I'm missing?
Thanks!
KAL

Kino 7 in backports wouldn't work at all.  The drop down menus wouldn't work, and keyboard commands froze everything up.  Capture would freeze if I even tried to click the tab.

---


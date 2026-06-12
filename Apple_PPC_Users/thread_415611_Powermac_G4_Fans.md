---
title: "Powermac G4 Fans"
date: 2007-04-20
forum: Apple PPC Users
---

### Post by Bootes on 2007-04-20
I've been running Ubuntu PPC Server on a 450mhz Powermac G4 for a couple months now. Everything has been going fine, except that the computer has become very noisy over the last couple days.  It appears that the fans are running at full speed all the time.  I've turned the computer off for a day, but when I turn it back on the fans go right back to full speed.  It was working fine not that long ago.  Is there anything I can do to make the computer less noisy?

Thanks for your help. :)

---

### Post by luckyd on 2007-04-21
It's probably a hardware probelem, although I don't know anything about servers you should probably open it up and get rid of any dust that may be in there. If that dosn't work... don't ask me.

---

### Post by stmiller on 2007-04-21
give me the output of 

$ lsmod

sounds like some thermal modules aren't loading for some reason.

---

### Post by Bootes on 2007-04-22
```

Module                  Size  Used by
binfmt_misc            13896  1 
appletalk              41340  20 
rfcomm                 45400  0 
l2cap                  26212  5 rfcomm
bluetooth              59012  4 rfcomm,l2cap
ppdev                  11268  0 
lp                     13612  0 
parport                44624  2 ppdev,lp
cpufreq_userspace       5588  0 
cpufreq_stats           6532  0 
cpufreq_powersave       2176  0 
cpufreq_ondemand        8128  0 
cpufreq_conservative     8448  0 
snd_powermac           49916  0 
snd_pcm_oss            54048  0 
snd_mixer_oss          22144  1 snd_pcm_oss
snd_pcm                95556  2 snd_powermac,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd                    69940  5 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11396  1 snd
snd_page_alloc         11368  1 snd_pcm
sbp2                   26440  0 
apm_emu                 8140  1 
sungem                 35492  0 
sungem_phy             10720  1 sungem
tsdev                   9120  0 
evdev                  12736  2 
uninorth_agp           11144  1 
agpgart                38204  1 uninorth_agp
ide_floppy             22784  0 
pmac_zilog             21060  0 
serial_core            24896  1 pmac_zilog
ext3                  161352  2 
jbd                    69556  1 ext3
ohci1394               41840  0 
ieee1394              431440  2 sbp2,ohci1394
ohci_hcd               24228  0 
usbcore               151676  2 ohci_hcd
ide_cd                 36420  0 
cdrom                  47932  1 ide_cd
aic7xxx               302704  0 
scsi_transport_spi     30912  1 aic7xxx
scsi_mod              175824  3 sbp2,aic7xxx,scsi_transport_spi
ide_disk               19296  5 
capability              5320  0 
commoncap               8064  1 capability

```

Thanks for your help.

---

### Post by stmiller on 2007-04-22
Okay add these to /etc/modules

therm-windtunnel
therm-adt746x

and reboot. See if that fixes it.

---

### Post by didg on 2007-04-25
therm-windtunnel? That's a 450 Mhz G4... What's the output of:

cat /proc/cpuinfo

It's spring....

---


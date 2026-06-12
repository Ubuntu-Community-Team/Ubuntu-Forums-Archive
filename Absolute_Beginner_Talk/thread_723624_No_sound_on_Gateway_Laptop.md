---
title: "No sound on Gateway Laptop"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by OldNewb on 2008-03-13
I'm trying to get Ubuntu running on a friends machine.  It is:

Gateway MX3410
With Ubuntu 7.10 installed and updated.

The laptop wiki says that for a similar model you have to update ALSA but I can't get that to work.

Please help.

---

### Post by dokdoom on 2008-03-13
On your command line, if you type alsam and hit TAB TAB will it tab out alsamixer? If not on the command line type:

apt-cache search alsamixer

 and look for the appropriate file.

---

### Post by OldNewb on 2008-03-13
> **dokdoom said:**
> On your command line, if you type alsam and hit TAB TAB will it tab out alsamixer? If not on the command line type:

apt-cache search alsamixer

 and look for the appropriate file.

It pulled up the mixer now what?

---

### Post by spiderbatdad on 2008-03-13
I assume the previous poster wanted you to check that Master and PCM were both up. If you still have problems, could you link to the wiki where you tried to follow instructions to upgrade. Also post the results of the commands ```
asoundconf list
lsmod
```Two separate entries.

---

### Post by OldNewb on 2008-03-14
fiyaro@fiyaro:~$ alsamixer 

fiyaro@fiyaro:~$ asoundconf list
Names of available sound cards:
NVidia

fiyaro@fiyaro:~$ lsmod
Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  4 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19592  0 
video                  18060  0 
ac                      6148  0 
battery                11012  0 
container               5504  0 
button                  8976  0 
dock                   10656  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  4 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
r8180                  89868  0 
ieee80211_rtl          80648  1 r8180
pcspkr                  4224  0 
psmouse                39952  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
nvidia               6221648  26 
shpchp                 34580  0 
i2c_nforce2             7040  0 
agpgart                35016  1 nvidia
k8temp                  6656  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  2 nvidia,i2c_nforce2
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_disk               18560  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
amd74xx                15260  0 [permanent]
ide_core              116804  3 ide_disk,ide_cd,amd74xx
ohci_hcd               22916  0 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
ehci_hcd               36492  0 
usbcore               138632  3 ohci_hcd,ehci_hcd
forcedeth              51592  0 
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


the wiki page is
[https://wiki.ubuntu.com/LaptopTestingTeam/GatewayMX3414](https://wiki.ubuntu.com/LaptopTestingTeam/GatewayMX3414)

---

### Post by superprash2003 on 2008-03-14
this may help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---


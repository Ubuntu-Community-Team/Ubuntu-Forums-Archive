---
title: "Update To Oblivion"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-11-20
A new system update has me in dire straights and I am considering returning to Windows. Upon installing the update this AM my monitor and grafics settings got completely screwed up. After playing with the system I was able to get my monitor reconfigured, but my graphiocs card an ATI 9550 is not being used. The restricted 3D driver is the issue. I have installed the frglx driver a few times, but it wont work. I am frustrated. Can anyone help??

Thx

---

### Post by jaybombalous on 2007-11-20
so un-install the update and and report it as a bug. :( U really didn't leave much for anyone to diagnose, good luck.

---

### Post by jaybombalous on 2007-11-20
have u tried 'envy'?

what does 

```
lsmod
```

give?

---

### Post by anaconda on 2007-11-20
You know..
I dont see any point in upgrading to each new kernel versions, because it just gives you problems without ANY advantages.

(I am assuming here that  the update updated your kernel.. and all your problems are caused by that.. like usual) 

 if the new kernel version doesn't give anything to you, then why change to it?

PS. I dont update my kernel very often, because then I would also have problems with NVIDIA, VMWare, and some other program, which I dont remember now..

---

### Post by scwinn on 2007-11-20
sheldon@sheldon-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  4 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vboxdrv                61104  0 
ppdev                  10244  0 
radeon                125472  2 
drm                    83348  3 radeon
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0 
dock                   10656  0 
video                  18060  0 
ac                      6148  0 
sbs                    19592  0 
container               5504  0 
battery                11012  0 
lp                     12580  0 
usblp                  15104  0 
snd_via82xx            29336  1 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
wlan_scan_sta          15104  1 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ath_rate_sample        14208  1 
serio_raw               8068  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             37412  1 
ath_pci                98336  0 
i2c_viapro             10004  0 
snd                    54660  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
psmouse                39952  0 
parport                37448  3 ppdev,lp,parport_pc
soundcore               8800  1 snd
i2c_core               26112  1 i2c_viapro
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
via_agp                11264  1 
agpgart                35016  2 drm,via_agp
wlan                  206660  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192720  3 ath_rate_sample,ath_pci
evdev                  11136  3 
iptable_nat             8708  0 
nf_nat                 20140  1 iptable_nat
nf_conntrack_ipv4      19724  2 iptable_nat
nf_conntrack           65288  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  0 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  2 iptable_nat,ip_tables
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
ata_generic             8452  0 
floppy                 60004  0 
via_rhine              25992  0 
mii                     6528  1 via_rhine
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usblp,ehci_hcd,uhci_hcd
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
sata_via               12548  0 
libata                125168  2 ata_generic,sata_via
scsi_mod              147084  1 libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
sheldon@sheldon-desktop:~$

---

### Post by jaybombalous on 2007-12-01
Do you have frglx being loaded as a daemon? I don't use ATI, so this is hard for me to diagnose for you, but I do know if frglx does not work its more then likely u have not configured it properly.

---

### Post by rickycodie on 2007-12-01
try doing a google search for the new ati linux drivers. see if installing those helps.

---

### Post by HermanAB on 2007-12-02
Re-install and then learn to not fix it if it ain't broke.  Most Linux problems are caused by finger trouble...

---

### Post by rickycodie on 2007-12-07
that's how i brake things most times

---


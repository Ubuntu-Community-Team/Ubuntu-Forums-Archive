---
title: "Sound goes off after some time"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by ankit07 on 2008-03-02
Hey,

My sound goes off after some time of playing audio or video file... The system sound test is working properly.. The sound returns after rebooting the system...
Any reason as to y it happens and How to solve it...

---

### Post by arimaniac on 2008-03-03
Hi there

Do you have 2 sound cards on????

Lets say an on board card and a PCI one????

This causes conflicts...

Do post back the output of 

```
sudo lsmod

sudo aplay -L
```

cheers...

---

### Post by ankit07 on 2008-03-05
No i dont think i have multiple sound cards... Anyway here r the outputs:

1.sudo lsmod

Module                  Size  Used by
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14080  0 
fat                    54300  1 vfat
usb_storage            73024  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
i915                   25856  2 
drm                    83348  3 i915
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
video                  18060  0 
container               5504  0 
button                  8976  0 
battery                11012  0 
lp                     12580  0 
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
intel_agp              25620  1 
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
agpgart                35016  3 drm,intel_agp
psmouse                39952  0 
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
sd_mod                 30336  5 
cdrom                  37536  1 sr_mod
ata_piix               17540  4 
ehci_hcd               36492  0 
ata_generic             8452  0 
e100                   37644  0 
mii                     6528  1 e100
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
uhci_hcd               26640  0 
usbcore               138632  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
capability              5896  0 
commoncap               8320  1 capability
fuse                   47124  7 


2.sudo aplay -L

default:CARD=Intel
    HDA Intel, STAC92xx Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

---

### Post by arimaniac on 2008-03-16
Nope no multiple sound card config,,,

Ok then it was just a guess....

Good luck with it...

---


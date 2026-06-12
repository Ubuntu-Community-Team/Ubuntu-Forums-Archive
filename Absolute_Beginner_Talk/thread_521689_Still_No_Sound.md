---
title: "Still No Sound"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by andy_6590 on 2007-08-09
Hello to whoever may read this. I have made a thread on this subject and getting nowhere with it. basically Ubuntu isn't reading my sound card and in result of this I am getting no sound. This was my first post:

[http://ubuntuforums.org/showthread.php?t=521226](http://ubuntuforums.org/showthread.php?t=521226) 

In this thread I was referred to this thread:

[http://ubuntuforums.org/showthread.php?t=365342](http://ubuntuforums.org/showthread.php?t=365342)

But still I have no sound. Does anyone know how to fix this problem. Help would be much appreciated. Thank you.

---

### Post by tbroderick on 2007-08-09
Try opening a terminal and run alsamixer. Does it detect you card? Look at the top left corner for a 'Card:' entry. What does it say?

---

### Post by andy_6590 on 2007-08-09
I typed in alsamixer in terminal and got this:

andrew@andrew-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
andrew@andrew-desktop:~$ 

Thank you.

---

### Post by tbroderick on 2007-08-09
Open a terminal and type
```
lsmod
```

Post the output.

---

### Post by andy_6590 on 2007-08-09
Here you go:

andrew@andrew-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
button                  8720  0 
container               5248  0 
asus_acpi              17308  0 
sbs                    15652  0 
video                  16388  0 
dock                   10268  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
battery                10756  0 
i2c_ec                  6016  1 sbs
nls_utf8                3072  1 
ntfs                  107764  1 
ipv6                  268960  10 
lp                     12452  0 
fuse                   46612  0 
snd_atiixp             20620  0 
snd_ac97_codec         98464  1 snd_atiixp
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
sg                     36252  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
sd_mod                 23428  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_atiixp,snd_pcm
i2c_piix4               9740  0 
i2c_core               22656  2 i2c_ec,i2c_piix4
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
af_packet              23816  2 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
ati_agp                10124  0 
agpgart                35400  1 ati_agp
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  4 
generic                 5124  0 [permanent]
usb_storage            72256  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
libusual               17936  1 usb_storage
sata_sil               12808  0 
atiixp                  7440  0 [permanent]
8139too                27648  0 
ata_generic             9092  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci_hcd               22532  0 
ehci_hcd               34188  0 
libata                125720  2 sata_sil,ata_generic
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
usbcore               134280  6 usb_storage,usbhid,libusual,ohci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
andrew@andrew-desktop:~$ 

Hope this helps.

---

### Post by tbroderick on 2007-08-09
Post the output of
```

sudo ls -l /dev/snd/*

```

---

### Post by andy_6590 on 2007-08-09
Here is the output of sudo ls -l /dev/snd/*:

andrew@andrew-desktop:~$ sudo ls -l /dev/snd/*
Password:
crw-rw---- 1 root audio 116, 3 2007-08-09 23:57 /dev/snd/seq
crw-rw---- 1 root audio 116, 2 2007-08-09 23:57 /dev/snd/timer
andrew@andrew-desktop:~$ 

Hope this helps. Thank you.

---


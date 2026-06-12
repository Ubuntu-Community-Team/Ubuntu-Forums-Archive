---
title: "USB External disk wont mount."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by squiggs on 2007-12-01
I have the following after issuing FDISK -l
I am trying to mount my 250GB disk - it has all my Itunes music on it.


paul@paul-desktop:~$ fdisk -l
paul@paul-desktop:~$ sudo fdisk -l
[sudo] password for paul:

Disk /dev/sda: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095056

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8624    69272248+  83  Linux
/dev/sda2            8625        8996     2988090    5  Extended
/dev/sda5            8625        8996     2988058+  82  Linux swap / Solaris

Disk /dev/sdb: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a6330

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8624    69272248+  83  Linux
/dev/sdb2            8625        8996     2988090    5  Extended
/dev/sdb5            8625        8996     2988058+  82  Linux swap / Solaris
paul@paul-desktop:~$ sudo fdisk -l

Disk /dev/sda: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095056

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8624    69272248+  83  Linux
/dev/sda2            8625        8996     2988090    5  Extended
/dev/sda5            8625        8996     2988058+  82  Linux swap / Solaris

Disk /dev/sdb: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a6330

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8624    69272248+  83  Linux
/dev/sdb2            8625        8996     2988090    5  Extended
/dev/sdb5            8625        8996     2988058+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6bce766

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30400   244187968+   7  HPFS/NTFS
paul@paul-desktop:~$ 
paul@paul-desktop:~$ clear

paul@paul-desktop:~$ sudo fdisk -l

Disk /dev/sda: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095056

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8624    69272248+  83  Linux
/dev/sda2            8625        8996     2988090    5  Extended
/dev/sda5            8625        8996     2988058+  82  Linux swap / Solaris

Disk /dev/sdb: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a6330

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8624    69272248+  83  Linux
/dev/sdb2            8625        8996     2988090    5  Extended
/dev/sdb5            8625        8996     2988058+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6bce766

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30400   244187968+   7  HPFS/NTFS

---

### Post by jken146 on 2007-12-01
Make a mount point:
```
sudo mkdir /media/sdc1
```
Mount the disk:
```
sudo mount /dev/sdc1 /media/sdc1
```

If you want to do this automatically every time you start up, you'll need to edit /etc/fstab (with sudo) - there are some howtos on these forums.

---

### Post by monte48lowes on 2007-12-01
It might be that the drive was not cleanly unmounted. If you have a windows box available, connect drive to the windows box and let it mount there, then cleanly unmount the drive. Try again on ubuntu.

Mike

---

### Post by jaybombalous on 2007-12-01
> HPFS/NTFS

you have the above file system on that device, first u must make sure u have support to mount such a file system. Then you can try the above advice and it should work if u have support for that file system.

do a...

```
lsmod
```

and post the results.

---

### Post by squiggs on 2007-12-03
Sorry Im a wee while coming back to you guys, To update, I plugged it into a windows box, and nothing, says would you like to format it. I think it may have got screwed whilst I was installing Linux. I can cope with reformatting it for the Linux file system if that helps.


Module                  Size  Used by
snd_rtctimer            4384  0 
binfmt_misc            12936  1 
ipv6                  273892  10 
af_packet              24840  4 
fglrx                 656352  3 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
container               5504  0 
sbs                    19592  0 
dock                   10656  0 
ac                      6148  0 
video                  18060  0 
button                  8976  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_intel8x0           34972  0 
snd_ac97_codec        100644  2 snd_emu10k1,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_pcm                80388  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
zd1211rw               53508  0 
snd_timer              24324  4 snd_rtctimer,snd_emu10k1,snd_pcm,snd_seq
ieee80211softmac       31360  1 zd1211rw
ieee80211              35656  2 zd1211rw,ieee80211softmac
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
emu10k1_gp              4736  0 
gameport               16776  2 emu10k1_gp
ieee80211_crypt         7040  1 ieee80211
snd                    54660  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_page_alloc         11400  3 snd_emu10k1,snd_intel8x0,snd_pcm
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                39952  0 
serio_raw               8068  0 
intel_agp              25620  0 
agpgart                35016  2 fglrx,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i82875p_edac            7172  0 
edac_mc                25808  1 i82875p_edac
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sd_mod                 30336  3 
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
floppy                 60004  0 
sata_promise           13956  2 
e100                   37644  0 
mii                     6528  1 e100
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_piix               17540  0 
libata                125168  3 ata_generic,sata_promise,ata_piix
scsi_mod              147084  5 sbp2,sd_mod,sg,sr_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 zd1211rw,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---


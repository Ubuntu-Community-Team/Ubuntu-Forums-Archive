---
title: "Player not mounting"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by vitalstatistix on 2007-05-10
When I connect a T.Sonic 610 mp3 player on edgy, it doesnt mount at all. The player shows its charging through the USB and is ready to receive files, but there is nothing under /media and no /dev/sda1 either. I am also unable to mount the player in Windows on my pc, though it works perfectly on a friend's. As a matter of fact I've never tried any USB device on this computer before. Any help would be appreciated.

---

### Post by Najand on 2007-05-10
When you connect it to the computer, try the following commands and send them to us here:
```

# lsusb
# dmesg | grep -i "SCSI device"
# sudo fdisk -l

```
"-l" is small "L".

---

### Post by vitalstatistix on 2007-05-10
Here you go: 

```
root@Best-001:/home/tatun# lsusb
root@Best-001:/home/tatun# dmesg | grep -i "SCSI device"
root@Best-001:/home/tatun# sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9732    57689415    f  W95 Ext'd (LBA)
/dev/hda3            9733        9733        8032+  83  Linux
/dev/hda5            2551        4948    19261903+   7  HPFS/NTFS
/dev/hda6            5101        6375    10241406    7  HPFS/NTFS
/dev/hda7            7651        9732    16723633+   7  HPFS/NTFS
/dev/hda8            6376        7650    10241406   83  Linux
/dev/hda9            4949        5099     1212876   82  Linux swap / Solaris
/dev/hda10           5100        5100        8001   83  Linux

Partition table entries are not in disk order

```

---

### Post by Najand on 2007-05-10
Wow seems your usb hub has not been installed at all.

---

### Post by vitalstatistix on 2007-05-10
> **Najand said:**
> Wow seems your usb hub has not been installed at all.

OK so what do I do now? There seem to be 4 USB ports on my pc, and none of them's working.

---

### Post by Najand on 2007-05-10
What is your:
```

# dmesg | grep -i "USB"

```??

---

### Post by vitalstatistix on 2007-05-10
There seems to be no output
```
root@Best-001:/home/tatun# dmesg | grep -i "USB"
root@Best-001:/home/tatun# 


```

---

### Post by Najand on 2007-05-10
Do you have ehci_hcd modprobed? check it using lsmod command.

---

### Post by vitalstatistix on 2007-05-10
I dont think so:

```
root@Best-001:/home/tatun# lsmod
Module                  Size  Used by
ipt_TCPMSS              4480  1 
xt_tcpmss               2560  1 
xt_tcpudp               3584  1 
iptable_filter          3328  1 
ip_tables              13128  1 iptable_filter
x_tables               14724  4 ipt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
pppoe                  13632  2 
pppox                   3976  1 pppoe
ppp_generic            28180  6 pppoe,pppox
slhc                    7552  1 ppp_generic
ipv6                  257632  10 
binfmt_misc            11784  1 
rfcomm                 38936  0 
hidp                   32000  2 
l2cap                  23300  10 rfcomm,hidp
bluetooth              48996  5 rfcomm,hidp,l2cap
i915                   20608  2 
drm                    72468  3 i915
speedstep_lib           4868  0 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  1 cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  0 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
af_packet              21768  2 
nls_utf8                2304  1 
ntfs                  108148  1 
dm_mod                 60088  9 
md_mod                 78740  0 
i2c_i801                8972  0 
eeprom                  7312  0 
fuse                   41864  6 
lp                     11972  0 
tsdev                   8256  0 
snd_intel8x0           33436  1 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
i2c_i810                5380  0 
snd_pcm_oss            46080  0 
i2c_algo_bit            9480  1 i2c_i810
e100                   36484  0 
snd_mixer_oss          18560  1 snd_pcm_oss
i2c_core               22288  4 i2c_ec,i2c_i801,eeprom,i2c_algo_bit
mii                     6016  1 e100
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
psmouse                40072  0 
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
evdev                  10496  1 
intel_agp              25116  1 
agpgart                33456  3 drm,intel_agp
serio_raw               7300  0 
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
floppy                 60676  0 
pcspkr                  3072  0 
rtc                    12596  0 
ext3                  138888  1 
jbd                    55700  1 ext3
ide_generic             1536  0 
ide_cd                 32416  0 
cdrom                  37792  1 ide_cd
ide_disk               17664  7 
piix                   10628  1 
generic                 5252  0 
thermal                14600  0 
processor              26028  1 thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability
root@Best-001:/home/tatun# 


```

---

### Post by vitalstatistix on 2007-05-15
Hello..........someone please help!!

---


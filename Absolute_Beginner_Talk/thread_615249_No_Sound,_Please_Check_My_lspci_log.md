---
title: "No Sound, Please Check My lspci log"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Squirrel Ninja on 2007-11-16
I just installed Ubuntu studio, most things seem to work but I currently have no sound, please check my log and give some advice, also tell me how to do what it is that you recommend, I'm not too familiar with the OS yet.  Also as a secondary issue, if I install my nividia driver, it will mess up the resolution, and sometimes not be able to boot, am I best just doing without?

```
alucard@Eva-Unit2:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

---

### Post by Mikecore on 2007-11-16
what is the output of 

>sudo lsmod

please post

---

### Post by Squirrel Ninja on 2007-11-16
Module                  Size  Used by
ipv6                  281444  10 
ppdev                  10244  0 
acpi_cpufreq           10696  1 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7488  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
video                  18060  0 
button                  9104  0 
container               5504  0 
battery                11012  0 
ac                      6276  0 
dock                   11124  0 
sbs                    19848  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     13252  0 
parport                38216  3 ppdev,parport_pc,lp
loop                   19588  0 
af_packet              25352  2 
snd_hda_intel         263840  0 
snd_pcm_oss            44928  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80644  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33792  0 
uvcvideo               49156  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
compat_ioctl32          2304  1 uvcvideo
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
bcm43xx               127848  0 
videodev               29568  1 uvcvideo
snd_seq                54128  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l1_compat            15364  2 uvcvideo,videodev
ieee80211softmac       31232  1 bcm43xx
sdhci                  18956  0 
i2c_core               26880  0 
v4l2_common            18560  2 uvcvideo,videodev
ieee80211              36040  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7168  1 ieee80211
snd_timer              24324  2 snd_pcm,snd_seq
mmc_core               28932  1 sdhci
joydev                 11456  0 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sr_mod                 17956  0 
cdrom                  37664  1 sr_mod
snd                    55172  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4352  0 
soundcore               9312  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
intel_agp              25748  0 
psmouse                40208  0 
agpgart                35284  1 intel_agp
serio_raw               8196  0 
shpchp                 34964  0 
pci_hotplug            33460  1 shpchp
evdev                  11136  5 
ata_piix               17668  0 
ext3                  134536  1 
jbd                    59688  1 ext3
mbcache                 9860  1 ext3
sg                     36764  0 
sd_mod                 30976  3 
ohci1394               37040  0 
ieee1394               98360  2 sbp2,ohci1394
b44                    28300  0 
mii                     6528  1 b44
ata_generic             8580  0 
ahci                   23556  2 
ehci_hcd               36108  0 
libata                125424  3 ata_piix,ata_generic,ahci
scsi_mod              148844  5 sbp2,sr_mod,sg,sd_mod,libata
uhci_hcd               26512  0 
usbcore               139912  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                14600  0 
processor              32200  2 acpi_cpufreq,thermal
fan                     5892  0 
fuse                   48404  1 
apparmor               41624  0 
commoncap               8320  1 apparmor



thanks a bunch

---

### Post by Mikecore on 2007-11-17
snd_hda_intel is your driver for your sound card. 

First make sure your volume is up and not muted.
second you can try removing the module and inserting it again sometimes that works.

to remove

sudo rmmod snd_hda_intel

to insert it again

sudo modprobe snd_hda_intel

if that doesn't work sometimes other modules or hardware prevent it from working your going to have to search the forums for other with the same issue. Mostly likely some one else has already had the problem and posted a fix.

---

### Post by Squirrel Ninja on 2007-11-17
When I type the command in, I get back
ERROR: Module snd_hda_intel does not exist in /proc/modules

---

### Post by Mikecore on 2007-11-19
Which command failed the remove or the insert?

---


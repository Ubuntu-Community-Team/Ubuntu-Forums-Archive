---
title: "bluetooth install 7.10"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by mookie_jones on 2007-11-16
I ive tried this and the wiki for installing a tecom bt3030 adapter to my laptop but im coming up with nothing. can someone help me with a link for what im doing wrong here?

---

### Post by Inxsible on 2007-11-16
what guide did you use?

what errors are you getting, if any?

Some information would be helpful.

---

### Post by mookie_jones on 2007-11-16
sorry, im new here

root@mookie-laptop:/home/mookie# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:00d1 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@mookie-laptop:/home/mookie# 


this is the only thing im coming up with information for

---

### Post by mookie_jones on 2007-11-16
root@mookie-laptop:/home/mookie# hcitool dev
Devices:
root@mookie-laptop:/home/mookie#

---

### Post by mookie_jones on 2007-11-16
ookie@mookie-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
vfat                   14080  1 
fat                    54300  1 vfat
usb_storage            73024  1 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
bnep                   17408  2 
bridge                 56088  0 
hidp                   21248  0 
wlan_tkip              13696  2 
af_packet              24840  4 
nls_cp437               6784  2 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  10 
rfcomm                 42136  6 
l2cap                  26240  15 bnep,hidp,rfcomm
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
container               5504  0 
battery                11012  0 
ac                      6148  0 
button                  8976  0 
video                  18060  11 
sbs                    19592  0 
dock                   10656  0 
sbp2                   24072  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
joydev                 11328  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
irda                  202300  0 
pcmcia                 41388  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt               3072  1 irda
pcspkr                  4224  0 
bcm203x                 7044  0 
hci_usb                18332  0 
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
wlan_scan_sta          15104  1 
usbhid                 29536  0 
psmouse                39952  0 
serio_raw               8068  0 
bluetooth              57060  7 bnep,hidp,rfcomm,l2cap,hci_usb
hid                    28928  2 hidp,usbhid
ath_rate_sample        14208  1 
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
ath_pci                98336  0 
wlan                  206660  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
nvidia               6221648  36 
ath_hal               192720  3 ath_rate_sample,ath_pci
i2c_core               26112  1 nvidia
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  5 
ata_piix               17540  3 
8139cp                 25088  0 
floppy                 60004  0 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 usb_storage,libusual,bcm203x,hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by mookie_jones on 2007-11-21
bumop

---

### Post by garnie on 2007-11-27
Also bumping since my situation is the exact same as yours

---

### Post by kidalabama on 2007-12-29
tecom bt3030 how can i run please. i am using ubuntu linux 7.10.

---


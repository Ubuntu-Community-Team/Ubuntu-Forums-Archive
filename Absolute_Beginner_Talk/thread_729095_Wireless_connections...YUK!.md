---
title: "Wireless connections...YUK!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by kam210 on 2008-03-19
Hey; I'm very much a newby to Ubuntu but I really like it and what it represents. 
I can't get the computer to recognize the wireless card (Belkin). There is a built in ethernet on the moboard that has worked just fine but I had to go to wireless, so here are some clues.

lshw
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 8
       bus info: pci@0000:00:08.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0a:e6:46:d5:e1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:46:D5:E1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xd800 

eth0:avah Link encap:Ethernet  HWaddr 00:0A:E6:46:D5:E1  
          inet addr:169.254.10.98  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

Can anyone help me please.

---

### Post by Hospadar on 2008-03-19
can you:
Give us the exact model name and version/revision number (if there is one) of your belkin device.

Also, post the output of "lsusb" (if it's a usb adapter) or "lspci" if it's a pci/pc card/express card adapter

Also, please post the output of "iwconfig"

Also, the output of "lsmod"

---

### Post by kam210 on 2008-03-19
Thanks for responding
All it says on the box is "Wireless G Desktop Card"

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
sd_mod                 30336  2 
usb_storage            73024  1 
libusual               18448  1 usb_storage
sg                     36764  0 
ipv6                  273892  8 
savage                 34176  2 
drm                    83348  3 savage
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
sbs                    19592  0 
ac                      6148  0 
container               5504  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
lp                     12580  0 
snd_via82xx            29336  1 
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401              9640  0 
snd_mpu401_uart         9600  2 snd_via82xx,snd_mpu401
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_timer              24324  2 snd_pcm,snd_seq
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
analog                 13344  0 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    54660  14 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
gameport               16776  2 snd_via82xx,analog
serio_raw               8068  0 
pcspkr                  4224  0 
psmouse                39952  0 
soundcore               8800  1 snd
i2c_prosavage           5248  0 
i2c_algo_bit            7428  1 i2c_prosavage
via_agp                11264  1 
via_ircc               27668  0 
irda                  202300  1 via_ircc
crc_ccitt               3072  1 irda
i2c_viapro             10004  0 
agpgart                35016  2 drm,via_agp
i2c_core               26112  3 i2c_prosavage,i2c_algo_bit,i2c_viapro
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
af_packet              24840  4 
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
floppy                 60004  0 
via_rhine              25992  0 
mii                     6528  1 via_rhine
via82cxxx              10372  0 [permanent]
ide_core              116804  4 usb_storage,ide_cd,ide_disk,via82cxxx
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  4 sd_mod,usb_storage,sg,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

Thanks

---

### Post by Hospadar on 2008-03-27
Hi, I believe this is what you need:
[http://ubuntuforums.org/showthread.php?t=95879](http://ubuntuforums.org/showthread.php?t=95879)

---


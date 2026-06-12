---
title: "No Sound"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by KraftSingle on 2008-03-11
I was doing some things to try to get my graphics working properly. I managed to fix my graphics and break my sound in one swift motion. To my dismay, later I noticed that when I fixed my graphics a totally new kernel with it's own recovery mode was created, which I had been using. The old kernel still has the graphics problem, but has sound, I believe. Anyway... here's links to what I did and some (possibly) useful info:

1st: [http://ubuntuforums.org/showthread.p...ht=KraftSingle](http://ubuntuforums.org/showthread.p...ht=KraftSingle)
2nd: [http://ubuntuforums.org/showthread.p...ht=KraftSingle](http://ubuntuforums.org/showthread.p...ht=KraftSingle)
Any help is appreciated. I should be standing by to watch for posts pretty much all evening.

---

### Post by spiderbatdad on 2008-03-11
It may not be too difficult to fix....You might be able to fix the latest kernel with all_generic_ide added as boot parameters. O r you might be able to modprobe your sound card. you could google ubuntu sound <your sound card> or look at launchpad for specific instructions relating to your sound card.  Maybe post : ```
lspci
``` for more help.

---

### Post by KraftSingle on 2008-03-11
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:04.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)

```

---

### Post by spiderbatdad on 2008-03-11
ok try ```
sudo modprobe snd-hda-intel
``` though it may be snd_hda_intel sorry i cant be more sure. also please post

```
lsmod
aplay -l
```

---

### Post by KraftSingle on 2008-03-11
```
Module                  Size  Used by
binfmt_misc            11400  1 
af_packet              21896  2 
ipv6                  257700  14 
fglrx                 653728  48 
rfcomm                 38684  2 
l2cap                  22788  11 rfcomm
bluetooth              52324  4 rfcomm,l2cap
capability              5000  0 
ppdev                   9348  0 
speedstep_lib           5380  0 
cpufreq_userspace       4116  0 
cpufreq_powersave       1792  0 
cpufreq_conservative     6560  0 
cpufreq_ondemand        8084  0 
cpufreq_stats           5508  0 
freq_table              4740  2 cpufreq_ondemand,cpufreq_stats
dock                    9476  0 
video                  17164  0 
sbs                    18568  0 
container               4608  0 
ac                      5252  0 
button                  8080  0 
battery                10116  0 
nls_iso8859_1           4224  1 
nls_cp437               5888  1 
vfat                   12800  1 
fat                    52636  1 vfat
sbp2                   23304  0 
lp                     11460  0 
cx88_blackbird         20740  0 
cx2341x                12420  1 cx88_blackbird
parport_pc             36132  1 
parport                35656  3 ppdev,lp,parport_pc
iTCO_wdt               10656  0 
psmouse                38672  0 
rtc                    13208  0 
pcspkr                  3072  0 
tuner                  62248  0 
cx8802                 18436  1 cx88_blackbird
iTCO_vendor_support     3972  1 iTCO_wdt
serio_raw               7044  0 
cx8800                 33784  1 cx88_blackbird
cx88xx                 66980  3 cx88_blackbird,cx8802,cx8800
ir_common              34436  1 cx88xx
i2c_algo_bit            6532  1 cx88xx
video_buf              25604  4 cx88_blackbird,cx8802,cx8800,cx88xx
tveeprom               15888  1 cx88xx
i2c_core               25104  4 tuner,cx88xx,i2c_algo_bit,tveeprom
videodev               28288  3 cx88_blackbird,cx8800,cx88xx
v4l1_compat            14468  1 videodev
compat_ioctl32          1408  1 cx8800
v4l2_common            17536  6 cx88_blackbird,cx2341x,tuner,cx8800,cx88xx,videodev
btcx_risc               5000  3 cx8802,cx8800,cx88xx
shpchp                 33556  0 
pci_hotplug            31288  1 shpchp
intel_agp              24596  0 
agpgart                33584  2 fglrx,intel_agp
evdev                  10240  3 
ext3                  129928  1 
jbd                    53416  1 ext3
mbcache                 8324  1 ext3
sg                     36124  0 
sd_mod                 29200  5 
sr_mod                 16548  0 
cdrom                  36512  1 sr_mod
8139too                26112  0 
ata_generic             7556  0 
usb_storage            71744  0 
ide_core              114772  1 usb_storage
libusual               17552  1 usb_storage
8139cp                 23680  0 
mii                     5632  2 8139too,8139cp
ohci1394               35760  0 
ieee1394               94904  2 sbp2,ohci1394
ata_piix               16644  4 
libata                125040  2 ata_generic,ata_piix
scsi_mod              146828  6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
ehci_hcd               35084  0 
uhci_hcd               25232  0 
usbcore               136088  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                13448  0 
processor              23984  1 thermal
fan                     4868  0 
commoncap               7424  1 capability
fuse                   44948  3 

```

---

### Post by spiderbatdad on 2008-03-11
a simple possibility is to run ```
asoundconf list
```This should give you a card parameter. then run ```
asoundconf set-default-card Parameter
```where Parameter is the out put of the first command. Reboot your system. This should work if the modules are existing.

---

### Post by KraftSingle on 2008-03-11
Thanks for all your help.
I entered the first command you gave me:
```
mark@mark-desktop:~$ sudo modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.
```

And these two... nothing happened
```
mark@mark-desktop:~$ asoundconf list
mark@mark-desktop:~$ asoundconf set-default-card Parameter
mark@mark-desktop:~$ 
```

---

### Post by spiderbatdad on 2008-03-11
ACK! That list looks terribly shy. I'm not sure what to suggest. You could try rebuilding Alsa. Is that the latest Hardy kernel or something?

Whatever, that kernel did not properly detect some of your hardware. You might be better off using the previous kernel from grub menu.

If you want to try to rebuild alsa: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by spiderbatdad on 2008-03-11
Exactly...asoundconf isnt going to find anything...your card doesn't exist as far as the kernel is concerned...see my previous post. If you need help using the previous kernel, we can try that, or you can follow the link to try to build Alsa.  Hopefully, you still have the previous kernel in /boot/grub/menu.lst

---


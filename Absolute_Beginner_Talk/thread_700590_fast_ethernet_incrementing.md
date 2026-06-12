---
title: "fast ethernet incrementing"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by new_bee_2_ubun2 on 2008-02-18
Hi I am new here and new to ubuntu. (Gutsy Gibbon)

I have managed to get the system running but have to reconfigure the network every time I boot. It also increments every boot eth0....eth1....eth2....eth (n) I am now at 21 :-)
I looked but I did not find an answer so if there is an answer please point me to it.

I hope this helps and thanks for your help 

uless_me   lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
dt@dt-laptop:~$  


cluless_me:~$ lsmod
Module                  Size  Used by
ipv6                  273892  10
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0
powernow_k8            16960  1
cpufreq_conservative     8072  0
cpufreq_stats           7232  0
cpufreq_ondemand        9612  0
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0
cpufreq_powersave       2688  0
container               5504  0
battery                11012  0
sbs                    19592  0
button                  8976  0
video                  18060  0
dock                   10656  0
ac                      6148  0
af_packet              24840  0
sbp2                   24072  0
parport_pc             37412  0
lp                     12580  0
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0
snd_hda_intel         263712  1
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_rawmidi            25728  1 snd_seq_midi
agpgart                35016  0
uvcvideo               48644  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
compat_ioctl32          2304  1 uvcvideo
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
i2c_core               26112  0
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_pci                98336  0
wlan                  206660  1 ath_pci
ide_cd                 32672  0
cdrom                  37536  1 ide_cd
ath_hal               192720  1 ath_pci
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  18828  0
mmc_core               28420  1 sdhci
pcspkr                  4224  0
soundcore               8800  1 snd
serio_raw               8068  0
psmouse                39952  0
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
k8temp                  6656  0
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
evdev                  11136  6
ext3                  133896  1
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sd_mod                 30336  3
usbhid                 29536  0
hid                    28928  1 usbhid
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
ahci                   23300  2
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0
forcedeth              51592  0
ata_generic             8452  0
libata                125168  2 ahci,ata_generic
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
ohci_hcd               22916  0
usbcore               138632  5 uvcvideo,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0
processor              32072  2 powernow_k8,thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor





eth21     Link encap:Ethernet  HWaddr 00:00:6C:84:35:83
          inet addr:192.168.178.2  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe84:3583/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5083213 (4.8 MB)  TX bytes:1507335 (1.4 MB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:704 (704.0 b)  TX bytes:704 (704.0 b)

---

### Post by njparton on 2008-02-20
You need to fix the mac address of you nic controller in the following file:

```
/etc/network/interfaces
```

add the following line to the ethX section (where X is the number you're up to!)

```
hwaddress ether XX:XX:XX:XX:XX:XX:XX
```

where XX:XX:XX:XX:XX:XX is the mac address of your nic.

Post your /etc/network/interfaces file here and I'll show you where to add it.  The mac address is shown under network tools under administration in the menus.

---

### Post by DarkMartyr on 2008-03-14
I tried this because I was having a similar problem on a similar computer. This solution did correct the mac address problem, but not after a reboot. After I rebooted it went up to the next eth# just like before and gave it a new mac address. My interfaces file has to be updated everytime to point to the next eth# that has been created upon reboot

---

### Post by adult swim on 2008-03-14
[http://ubuntuforums.org/showthread.php?t=723813](http://ubuntuforums.org/showthread.php?t=723813)
[http://ubuntuforums.org/showthread.php?t=723917](http://ubuntuforums.org/showthread.php?t=723917)
3 threads?

---

### Post by DarkMartyr on 2008-03-14
My original. One started by someone helping me. This one started by someone with a similar problem, I think I would help my letting others know this didn't fix the problem. That way they wouldn't have to waste there time on this fix like me.

---

### Post by StrayCat on 2008-03-14
I bought a brandnew hp laptop two days ago and I am experiencing exactly the same thing running ubuntu/LinuxMInt: Changing MAC address of the network adapter and incrementing ethx at every reboot... Bad thing if you have a fixed IP and have to configure your interface after every restart... :(
My solution was (for the time being) creating a S01something-script in rc0.d and rc6.d which goes:

#! /bin/sh
rm /etc/udev/rules.d/70-perstistent-net.rules

This removes the respective file at reboot/shutdown and the system always detects a fresh interface **eth0** during boot.
Nevertheless the changing MAC of the network adapter worries me. I couldn't find a lot on the net. I'd like to know wether this is something you can live with or a sign of some serious damage... I don't dare talking to the hp-people because they'll probably cut off communication as soon as I mention something like "...erased vista... ...installed linux..."

---


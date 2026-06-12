---
title: "2008 White Macbook Wireless issues (Broadcom 4328)"
date: 2008-12-18
forum: Apple Hardware Users
---

### Post by HelpdeskSean on 2008-12-18
I've been dreding the forums for hours now, and can't seem to find a resolution to this issue.  I have a Macbook with the Broadcom 4328 wireless device. The WL driver is loading properly, and the device shows up as eth1, but when I try to connect to my work AP (WPA2-Enterprise), it prompts over and over again for authentication.

Now, I'm unsure if it's even trying to connect to the AP, as if I look at the ifconfig info after a few connection attempts, I get:

```

eth1      Link encap:Ethernet  HWaddr 00:21:e9:df:a2:bf  
          inet6 addr: fe80::221:e9ff:fedf:a2bf/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:183
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16  

```

The 0/0 RX/TX packets and 6 errors leads me to believe that it's not even trying to connect.

More info below:

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

lsmod
```

Module                  Size  Used by
wl                   1085520  0 
ipv6                  314312  10 
ieee80211_crypt_tkip    18048  0 
ieee80211_crypt        14596  2 wl,ieee80211_crypt_tkip
af_packet              29568  4 
i915                   44544  2 
drm                   110304  3 i915
binfmt_misc            18700  1 
btusb                  21912  3 
rfcomm                 51104  2 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  16 rfcomm,bnep
bluetooth              70820  11 btusb,rfcomm,sco,bnep,l2cap
uinput                 17408  2 
ppdev                  16904  0 
acpi_cpufreq           16400  1 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
cpufreq_userspace      12420  0 
cpufreq_ondemand       16400  1 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    16392  0 
container              12288  0 
wmi                    15808  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
sbp2                   32652  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
uvcvideo               68616  0 
compat_ioctl32         18176  1 uvcvideo
iTCO_wdt               21072  0 
videodev               46720  2 uvcvideo,compat_ioctl32
iTCO_vendor_support    12420  1 iTCO_wdt
snd_hda_intel         489264  3 
pcspkr                 11136  0 
v4l1_compat            24580  2 uvcvideo,videodev
evdev                  20512  16 
appletouch             18564  0 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
appleir                13440  0 
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
video                  28948  0 
battery                21128  0 
output                 11776  1 video
shpchp                 42140  0 
ac                     13448  0 
button                 15904  0 
intel_agp              39280  1 
pci_hotplug            39472  1 shpchp
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
loop                   26380  2 
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  2 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
ata_generic            14212  0 
pata_acpi              13568  0 
usbhid                 39776  0 
hid                    59072  1 usbhid
ata_piix               29444  1 
libata                200160  3 ata_generic,pata_acpi,ata_piix
scsi_mod              183160  5 sbp2,sr_mod,sd_mod,sg,libata
ohci1394               41524  0 
ieee1394              110592  2 sbp2,ohci1394
dock                   18464  1 libata
sky2                   61444  0 
ehci_hcd               48908  0 
uhci_hcd               34336  0 
usbcore               175376  8 btusb,uvcvideo,appletouch,appleir,usbhid,ehci_hcd,uhci_hcd
thermal                27424  0 
processor              47800  4 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5 

```

Thanks if anyone has a nudge in the right direction.

---

### Post by xjcannonx on 2008-12-18
1. What version of ubuntu are you running

2. I believe your card requires ndiswrapper

2. what is tho output of ```
sudo iwlist scanning
```

---

### Post by HelpdeskSean on 2008-12-18
> **xjcannonx said:**
> 1. What version of ubuntu are you running

2. I believe your card requires ndiswrapper

2. what is tho output of ```
sudo iwlist scanning
```



Ubuntu 8.10

iwlist scanning:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:92:36:42:70
                    ESSID:"acadia"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-40 dBm  Noise level:-93 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:11:92:36:51:90
                    ESSID:"acadia"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-67 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

I'm pretty sure that the Broadcom 4328 is supported by the Broadcom STA driver, as it says it's supported in the restricted driver manager, and this is reflected from a lot of what I've read today.

Thanks for the input.

---

### Post by xjcannonx on 2008-12-18
Can you please provide the steps you took or thu guides you used?

---

### Post by HelpdeskSean on 2008-12-18
> **xjcannonx said:**
> Can you please provide the steps you took or thu guides you used?

I have my Mac configured with Boot Camp to allow MacOS and Windows.  In Windows, I installed Ubuntu 8.10 using Wubi.  This gives me MacOS, Windows and Ubuntu in an easy-to-explain manner (I'm actually doing this in an attempt to create an "accepted" manner for my students to install all 3, as some are not sure if they wish to keep Ubuntu, etc and this is the easiest to reverse vs rEFIt and added partitions).

This works very slick, and when you hold ALT OPTION on boot, you can choose MacOS or Windows, and if you choose Windows, the Windows boot loader prompts you for a choice between Windows or Ubuntu. 

I installed Ubuntu, and without changing anything or running through any guides, everything visible worked out of box (Video w/ DRI, NIC, bluetooth, sound, etc) with the exception of wireless.  I went into the Restricted Driver UI as prompted, and enabled the Broadcom STA driver.

I now get eth1, which can see my access points in a scan list, and it knows its a WPA2-Ent encrypted device, but never seems to authenticate or get an IP.

This is everything, in absolute entirety, that I've done up to this point.  If anyone has any clues, I'm eager to hear from them.

---

### Post by xjcannonx on 2008-12-18
I will look into it more when i get home, but it would be interesting to see if you can connect to an unsecured network...

---

### Post by cyberdork33 on 2008-12-19
there have been issues with several cards connecting to certain encrypted networks. I would try to see if the unsecured network works well. If that is the case, then it is definitely the encryption holding you up and in that case I would try different drivers (ndiswrapper) and maybe try using wicd instead of network-manager (which some have reported fixes this problem.)

---

### Post by xjcannonx on 2008-12-19
Just a guess, but since you are using the wl driver you might want to make sure the default drivers are not loading, if they are you can use ```
rmmod bcm43xx
rmmod b43
rmmod b43legacy
```
To stop them

---


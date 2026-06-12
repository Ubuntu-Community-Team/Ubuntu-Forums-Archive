---
title: "Wireless Woes"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2008-02-01
Some months ago, I was able to salvage an Acer TravelMate C110 out of the trash.

[http://reviews.cnet.com/tablet-pcs/acer-travelmate-c110/4505-3126_7-21188968.html](http://reviews.cnet.com/tablet-pcs/acer-travelmate-c110/4505-3126_7-21188968.html)

A few screws, some TLC, and fresh install of Ubuntu (I could see why some one threw it out, when I tried to boot it in XP it was virtually unusable, too much spy ware and viruses) and I had myself a super small light weight notebook.  Everything works fine ( I was even able to get the touch screen to work) except the wireless.

It doesn't like to connect to most networks.  It connects to my wireless fine at home, I've hit a T-mobile hotspot that seemd to work ok, but I'm at work now and can't seem to get onto our wireless network (Yes, I'm sure I'm using the correct WEP key).  I've also tried to connect to a few ungaurded wireless networks around my apartment complex without any luck.  It detects the networks just fine, just can't seem to connect.  Anybody have any suggestions?

Thanks!

---

### Post by jan quark on 2008-02-01
it would be helpful to know the wireless card name

type the following into the terminal

```
iwconfig
```
```
ifconfig
```
```
lspci | grep Ethernet
```
```
sudo iwlist scan
```

and post the results

---

### Post by marmaladejackson on 2008-02-01
```
brian@brian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

brian@brian-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:04:67:D0  
          inet addr:192.168.0.183  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe04:67d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:4 txqueuelen:1000 
          RX bytes:755886 (738.1 KB)  TX bytes:146315 (142.8 KB)

eth1      Link encap:Ethernet  HWaddr 00:04:23:92:AF:1F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 Memory:d0200000-d0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

brian@brian-laptop:~$ lspci | grep Ethernet
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
brian@brian-laptop:~$ sudo iwlist scan
[sudo] password for brian:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:06:25:4B:56:51
                    ESSID:"COMPANY2"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:58  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1216ms ago
          Cell 02 - Address: 00:90:4C:60:04:00
                    ESSID:"COMPANY1"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:53  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3504ms ago
          Cell 03 - Address: 00:0D:3A:2B:89:E6
                    ESSID:"OFFICE"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality:42  Signal level:0  Noise level:0
                    Extra: Last beacon: 1160ms ago
          Cell 04 - Address: 00:16:B6:51:D1:B5
                    ESSID:"grandview"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:68  Signal level:0  Noise level:0
                    Extra: Last beacon: 564ms ago
          Cell 05 - Address: 00:17:3F:9F:50:8C
                    ESSID:"CrownAP"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    Extra: Last beacon: 1660ms ago
          Cell 06 - Address: 00:1A:70:EF:F3:83
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:18  Signal level:0  Noise level:0
                    Extra: Last beacon: 572ms ago

brian@brian-laptop:~$ 

```

---

### Post by marmaladejackson on 2008-02-03
Ok, trying a different tack.  Bought the cheapest wireless PC card adapter I could find, an Airlink 101.  Installed the indswrapper and from what I can tell it is up and functional.  How would I go about disableing the on board wireless in favor of the PC card?  I thought I would be able to do it via the BIOS, but that disables all the wireless (or perhaps it does just disable the on board wireless, but the PC card is not enabled as the primary adapter).

As always, thanks!

-B

---

### Post by jan quark on 2008-02-03
to disable the card we have to do the following:

we have to disable the module which controls the card

run in terminal

```
lsmod | grep intel
```

or to list all modules, because I am guessing dont know the exact name of the intel module
```

lsmod
```

and post the results

when we have found the module

we have to add it to the blacklist file

run in terminal
```

sudo gedit /etc/modprobe.d/blacklist
```

add the module you want to disable by adding the line

blacklist name of module

and save

that should do it

---

### Post by marmaladejackson on 2008-02-03
ok... here is lsmod:

```
brian@brian-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
speedstep_centrino      8256  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
freq_table              5792  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
container               5504  0 
video                  18060  0 
dock                   10656  0 
sbs                    19592  0 
ac                      6148  0 
button                  8976  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
joydev                 11328  0 
ipw2100                72240  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 41388  0 
ieee80211              35656  1 ipw2100
ieee80211_crypt         7040  1 ieee80211
snd                    54660  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               8800  1 snd
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
serio_raw               8068  0 
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
ata_generic             8452  0 
e100                   37644  0 
mii                     6528  1 e100
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

### Post by marmaladejackson on 2008-02-03
is it ieee80211?

That and ieee80211_crypt are the only two that I can see that might have something to do with wireless.

---

### Post by jan quark on 2008-02-03
I guess it should be the module

ipw2100

add 
blacklist ipw2100 

as mentioned above

---

### Post by marmaladejackson on 2008-02-03
OK... I'll give it a whirl!

---

### Post by marmaladejackson on 2008-02-03
OK... blacklisting ipw200 disabled all the wireless function.  So now how do I "turn on" or use the Airlink?

Thanks!

---


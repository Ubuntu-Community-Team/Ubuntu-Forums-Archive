---
title: "Still having trouble with my wireless"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by hossiam on 2008-03-31
linksys WPC11 ver 3 ........is what im trying to use in 7.10 but cannot seem to get it to work.   Any help would be great.......I new at this linux thing so the more layman the answer the better.  thanks again

---

### Post by Inxsible on 2008-03-31
> **hossiam said:**
> linksys WPC11 ver 3 ........is what im trying to use in 7.10 but cannot seem to get it to work.   Any help would be great.......I new at this linux thing so the more layman the answer the better.  thanks againI am going to recommend this to the unanswered posts team. Hopefully someone will help you out soon.

---

### Post by privaterolf on 2008-03-31
If it's broadcom, I haven't gotten my built-in wireless to work on my laptop.

Luckily, I had a Belkin 7050FSD USB adapter lying around, worked without downloading any drivers.

---

### Post by atibs1 on 2008-03-31
This has got me too. Gutsy with linksys WPC11 Ver3

---

### Post by anewguy on 2008-03-31
Please go in to a terminal window and post the output of the following back here:

lspci


lsusb


We'll go from there.....:)

---

### Post by atibs1 on 2008-04-01
user@user-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M


user@user-laptop:~$ lsmod
Module                  Size  Used by
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  0 
ipv6                  273892  8 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
video                  18060  0 
button                  8976  0 
sbs                    19592  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
ac                      6148  0 
ndiswrapper           193436  0 
sbp2                   24072  0 
lp                     12580  0 
joydev                 11328  0 
hostap_cs              63252  3 
hostap                114436  1 hostap_cs
ieee80211_crypt         7040  2 ieee80211_crypt_wep,hostap
snd_ali5451            24460  1 
snd_ac97_codec        100644  1 snd_ali5451
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
pcmcia                 41388  1 hostap_cs
snd_rawmidi            25728  1 snd_seq_midi
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               8068  0 
psmouse                39952  0 
i2c_ali15x3             9092  0 
i2c_ali1535             8196  0 
i2c_core               26112  2 i2c_ali15x3,i2c_ali1535
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
snd_page_alloc         11400  1 snd_pcm
ati_agp                10124  1 
agpgart                35016  2 drm,ati_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
pcmcia_core            40980  4 hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
alim15x3               12556  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,alim15x3
floppy                 60004  0 
natsemi                31328  0 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sbp2,libata
ehci_hcd               36492  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
uhci_hcd               26640  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor




user@user-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


user@user-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:85:07:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7841 (7.6 KB)  TX bytes:7841 (7.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-06-25-15-6A-74-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

wlan0     Link encap:Ethernet  HWaddr 00:06:25:15:6A:74  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 




I previously followed the instructions contained in this thread   [http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc](http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc) 
to successfully install a linksys wusb54gc  It looks like some of it may still be hanging around.  Thanks for your help with this.

---

### Post by ajmorris on 2008-04-01
hi there,
the easiest way to get that pcmcia card to work, is via Ndiswrapper with the Broadcom 4311 Drivers. so apt-get install ndiswrapper, and download the windows Broadcom 4311 Drivers, (go with the XP not vista)
then:
```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l (to make sure it worked)
sudo depmod -a
sudo modprobe ndiswrapper
``` 

then sudo iwconfig should list wlan0 as a network interface.

AJ

---

### Post by atibs1 on 2008-04-07
Ajmorris
Thanks for the guidance,  I dug in and found this thread    [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-2b435303abdabe070c57502f8afbb765bc56ad57](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-2b435303abdabe070c57502f8afbb765bc56ad57)  and it led to me getting a wpc54g to work.   The wpc11 v3 is indicated to have a prism1 chip set rather than the broadcom. ( I referenced this link regarding wifi cards and their chipsets   [http://linux-wless.passys.nl/query_part.php?brandname=Linksys](http://linux-wless.passys.nl/query_part.php?brandname=Linksys)  )     The wpc11 v3  is going to be stuck doing windows duty as I had no luck using the 4311 drivers.  Thanks, Drew.

---

### Post by iamclueless on 2008-04-08
> **atibs1 said:**
> Ajmorris
Thanks for the guidance,  I dug in and found this thread    [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-2b435303abdabe070c57502f8afbb765bc56ad57](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-2b435303abdabe070c57502f8afbb765bc56ad57)  and it led to me getting a wpc54g to work.   The wpc11 v3 is indicated to have a prism1 chip set rather than the broadcom. ( I referenced this link regarding wifi cards and their chipsets   [http://linux-wless.passys.nl/query_part.php?brandname=Linksys](http://linux-wless.passys.nl/query_part.php?brandname=Linksys)  )     The wpc11 v3  is going to be stuck doing windows duty as I had no luck using the 4311 drivers.  Thanks, Drew.

can someone else confirm this?  ive been digging through the forum to try and get my wpc11 v3  to work for the whole day now with no luck.  

the ubuntu docs says it should work out of the box (obviously it doesnt).  is there someone who has managed to get it to work. mine only works on unsecured signals

---

### Post by Het Irv on 2008-05-13
Did you try NDISWrapper with the drivers that came with the card?

---


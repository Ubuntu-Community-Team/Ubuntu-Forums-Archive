---
title: "Need help with Internet connection"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by msredfootmomof3 on 2007-06-02
I need help configuring my internet connection.  I have a LAN.  The computer shows that I am connected, but I do not have the internet.  I checked iwconfig and received the RX invalid nwid and invalid crypt  I am not sure how to exactly configure this. I am new to this. I have a dual boot with Windows XP and a linski wireless card to connect to a belkin router.  Any help would be appreciated.  Please email me.

---

### Post by handydan918 on 2007-06-02
Open up a terminal window and post the output of the following commands:
lspci

lsmod

sudo dhclient

That should give us enough info to start...
moderator;
Shouldn't there be a sticky about what info to include with these wireless questions? Or did I miss it? (along with everyone who posts without including basic info!);)

---

### Post by e_james on 2007-06-02
handydan918

Maybe I'm reinventing a wheel I haven't noticed yet, but I would like to see a wiki topic for wireless and general internet troubleshooting to which all the enquiries could be directed. There are so many questions requiring roughly the same answers. If all possible answers were collected in the one area, surely it would be a good idea? There is something along these lines in the ubuntu wiki, but they don't seem to want edits from users with limited expertise. My main problem with GNU/Linux is the enormous gap between "works out of the box" and "needs a bit of tweaking". In recent months I have followed detailed instructions with the following results..

1. It works, but I don't know why.
2. I do everything as specified (I think), but it doesn't work.
3. I get part way through and find that the instructions no longer apply to my situation.
4. At least one part of the instructions requires a greater knowledge of the situation than I currently possess.

I am a great believer in the hypertext concept for instruction manuals. If an item needs explanation, link to a new page. If you don't need the explanation, you don't read it.

---

### Post by kernel tom on 2007-06-02
try opening a terminal and run

sudo dhclient eth0

should connect you

---

### Post by handydan918 on 2007-06-02
> **kernel tom said:**
> try opening a terminal and run

sudo dhclient eth0

should connect you

True, if his wireless is on eth0...
otherwise, a simple dhclient command should attempt all configured interfaces.

---

### Post by handydan918 on 2007-06-02
> **e_james said:**
> handydan918

Maybe I'm reinventing a wheel I haven't noticed yet, but I would like to see a wiki topic for wireless and general internet troubleshooting to which all the enquiries could be directed. There are so many questions requiring roughly the same answers. If all possible answers were collected in the one area, surely it would be a good idea? There is something along these lines in the ubuntu wiki, but they don't seem to want edits from users with limited expertise. My main problem with GNU/Linux is the enormous gap between "works out of the box" and "needs a bit of tweaking". In recent months I have followed detailed instructions with the following results..

1. It works, but I don't know why.
2. I do everything as specified (I think), but it doesn't work.
3. I get part way through and find that the instructions no longer apply to my situation.
4. At least one part of the instructions requires a greater knowledge of the situation than I currently possess.

I am a great believer in the hypertext concept for instruction manuals. If an item needs explanation, link to a new page. If you don't need the explanation, you don't read it.

Good points, all. I wonder if someone could point us to where such suggestions are best made?
Besides, everyone has limited expertise. It's just a matter of where the limits are...;)

---

### Post by msredfootmomof3 on 2007-06-02
Here is what I have. I really appreciate any help.  

julie@julie-desktop:~$ lspci 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02) 
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) 
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) 
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82) 
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) 
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) 
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02) 
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) 
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) 
00:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31) 
julie@julie-desktop:~$ lsmod 
Module                  Size  Used by 
nls_cp437               6784  1 
isofs                  36284  1 
udf                    85252  0 
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm 
bluetooth              55908  4 rfcomm,l2cap 
apm                    22752  1 
ppdev                  10116  0 
sis                     8576  2 
drm                    81044  3 sis 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats 
cpufreq_conservative     8200  0 
af_packet              23816  0 
nls_utf8                3072  1 
ntfs                  107764  1 
lp                     12452  0 
fuse                   46612  0 
sg                     36252  0 
sr_mod                 17060  1 
snd_trident            44548  1 
snd_ac97_codec         98336  1 snd_trident 
ac97_bus                3200  1 snd_ac97_codec 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss 
snd_pcm                79876  3 snd_trident,snd_ac97_codec,snd_pcm_oss 
snd_page_alloc         10888  2 snd_trident,snd_pcm 
snd_util_mem            5760  1 snd_trident 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
serio_raw               7940  0 
analog                 12832  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc 
gameport               16520  3 snd_trident,analog 
snd_mpu401              9256  0 
snd_mpu401_uart         9472  2 snd_trident,snd_mpu401 
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart 
rt61                  245128  1 
psmouse                38920  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              23684  2 snd_pcm,snd_seq 
snd_seq_device          9100  6 snd_trident,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
pcspkr                  4224  0 
sis_agp                 9604  1 
i2c_sis630              8588  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp 
agpgart                35400  2 drm,sis_agp 
snd                    54020  14 snd_trident,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               8672  1 snd 
i2c_core               22784  1 i2c_sis630 
tsdev                   8768  0 
evdev                  11008  1 
ext3                  133128  1 
jbd                    59816  1 ext3 
mbcache                 9604  1 ext3 
usb_storage            72256  1 
libusual               17936  1 usb_storage 
ide_cd                 32672  0 
cdrom                  37664  2 sr_mod,ide_cd 
ide_disk               17024  4 
ata_generic             9092  0 
pata_sis               14220  0 
libata                125720  2 ata_generic,pata_sis 
scsi_mod              142348  4 sg,sr_mod,usb_storage,libata 
floppy                 59524  0 
ohci_hcd               22532  0 
usbcore               134280  4 usb_storage,libusual,ohci_hcd 
sis900                 24704  0 
mii                     6528  1 sis900 
sis5513                14856  0 [permanent] 
generic                 5124  0 [permanent] 
fbcon                  42656  0 
tileblit                3584  1 fbcon 
font                    9216  1 fbcon 
bitblit                 6912  1 fbcon 
softcursor              3200  1 bitblit 
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability 
julie@julie-desktop:~$ sudo dhclient 
Password: 
Sorry, try again. 
Password: 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/ra1/00:18:f8:34:38:35 
Sending on   LPF/ra1/00:18:f8:34:38:35 
Listening on LPF/eth0/00:d0:09:f1:37:49 
Sending on   LPF/eth0/00:d0:09:f1:37:49 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 8 
DHCPOFFER from 192.168.2.1 
DHCPREQUEST on ra1 to 255.255.255.255 port 67 
DHCPACK from 192.168.2.1 
bound to 192.168.2.3 -- renewal in 966654231 seconds. 
julie@julie-desktop:~$ 
julie@julie-desktop:~$

---


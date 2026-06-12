---
title: "can´t get ip in wireless network"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Pulka on 2008-01-31
Hi!

Have a wireless connection that works fine in windows, but in ubuntu, it can´t get an ip. The card is recognized, another wireless networks show up, what´s wrong?
Here are the results of some commands:


ndiswrapper -l
The program 'ndiswrapper' is currently not installed. You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found


lshw -C network
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: L2 100 Mbit Ethernet Adapter
vendor: Attansic Technology Corp.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: a0
serial: 00:1d:60:29:b6:38
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 module=atl2 multicast=yes
*-network
description: Wireless interface
product: RT2561/RT61 rev B 802.11g
vendor: RaLink
physical id: 0
bus info: pci@0000:01:00.0
logical name: wmaster0
version: 00
serial: 00:1b:11:bf:63:e1
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g



lsmod
Module Size Used by
nls_iso8859_1 5120 1 
nls_cp437 6784 1 
vfat 14080 1 
fat 54300 1 vfat
i915 25856 2 
drm 83348 3 i915
rfcomm 42136 2 
l2cap 26240 11 rfcomm
bluetooth 57060 4 rfcomm,l2cap
ppdev 10244 0 
speedstep_lib 6404 0 
cpufreq_stats 7232 0 
cpufreq_conservative 8072 0 
cpufreq_ondemand 9612 0 
cpufreq_powersave 2688 0 
cpufreq_userspace 5280 0 
freq_table 5792 2 cpufreq_stats,cpufreq_ondemand
ac 6148 0 
container 5504 0 
video 18060 0 
sbs 19592 0 
button 8976 0 
dock 10656 0 
battery 11012 0 
af_packet 24840 4 
sbp2 24072 0 
lp 12580 0 
snd_emu10k1_synth 8192 0 
snd_emux_synth 35456 1 snd_emu10k1_synth
snd_seq_virmidi 8064 1 snd_emux_synth
snd_seq_midi_emul 7680 1 snd_emux_synth
snd_hda_intel 263712 0 
snd_emu10k1 137248 1 snd_emu10k1_synth
snd_ac97_codec 100644 1 snd_emu10k1
snd_seq_dummy 4740 0 
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44672 0 
arc4 2944 2 
snd_mixer_oss 17664 1 snd_pcm_oss
ecb 4608 2 
blkcipher 7556 1 ecb
snd_seq_oss 33152 0 
rc80211_simple 6912 1 
snd_seq_midi 9600 0 
snd_pcm 80388 4 snd_hda_intel,snd_emu10k1,snd_ac97_codec,snd_pcm_o ss
snd_util_mem 5760 2 snd_emux_synth,snd_emu10k1
usblp 15104 0 
atl2 33304 0 
snd_rawmidi 25728 3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event 8448 3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_hwdep 10244 2 snd_emux_synth,snd_emu10k1
rt61pci 24576 0 
rt2x00pci 11520 1 rt61pci
rt2x00lib 19584 2 rt61pci,rt2x00pci
rfkill 8208 1 rt2x00lib
mac80211 171016 4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib
cfg80211 7304 1 mac80211
input_polldev 5896 1 rt2x00lib
crc_itu_t 3072 1 rt2x00lib
eeprom_93cx6 3200 1 rt61pci
xpad 9988 0 
snd_seq 53232 9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,s nd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi _event
snd_timer 24324 3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device 9228 8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_s eq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_ seq
psmouse 39952 0 
parport_pc 37412 1 
emu10k1_gp 4736 0 
gameport 16776 2 emu10k1_gp
iTCO_wdt 11940 0 
snd 54660 14 snd_emux_synth,snd_seq_virmidi,snd_hda_intel,snd_e mu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,sn d_seq_oss,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,sn d_timer,snd_seq_device
shpchp 34580 0 
pci_hotplug 32704 1 shpchp
serio_raw 8068 0 
parport 37448 3 ppdev,lp,parport_pc
intel_agp 25620 1 
iTCO_vendor_support 4868 1 iTCO_wdt
pcspkr 4224 0 
soundcore 8800 1 snd
snd_page_alloc 11400 3 snd_hda_intel,snd_emu10k1,snd_pcm
agpgart 35016 3 drm,intel_agp
evdev 11136 4 
ext3 133896 4 
jbd 60456 1 ext3
mbcache 9732 1 ext3
sg 36764 0 
sd_mod 30336 9 
sr_mod 17828 0 
cdrom 37536 1 sr_mod
usb_storage 73024 1 
ide_core 116804 1 usb_storage
ata_piix 17540 5 
usbhid 29536 0 
hid 28928 1 usbhid
libusual 18448 1 usb_storage
ata_generic 8452 0 
libata 125168 2 ata_piix,ata_generic
scsi_mod 147084 6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
ohci1394 36528 0 
ieee1394 96312 2 sbp2,ohci1394
floppy 60004 0 
uhci_hcd 26640 0 
ehci_hcd 36492 0 
usbcore 138632 8 usblp,xpad,usb_storage,usbhid,libusual,uhci_hcd,eh ci_hcd
thermal 14344 0 
processor 32072 1 thermal
fan 5764 0 
fuse 47124 1 
apparmor 40728 0 
commoncap 8320 1 apparmor



Can anyone find what is the problem?

---

### Post by jan quark on 2008-01-31
pls post the restults of these commands

ifconfig
iwconfig
lspci | grep Ethernet
sudo iwlist scan

---

### Post by Pulka on 2008-01-31
**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:1D:60:29:B6:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3795 (3.7 KB)  TX bytes:3795 (3.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:11:BF:63:E1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:1B:11:BF:63:E1  
          inet addr:169.254.8.108  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-11-BF-63-E1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


 **iwconfig**

lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"djedje"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


** lspci | grep Ethernet**

02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)



 **sudo iwlist scan**

lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:ED:E2:D9
                    ESSID:"PBAMWLan"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-72 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001a8da5751c7
          Cell 02 - Address: 00:13:10:49:83:4C
                    ESSID:"intro"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-76 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000012549301d1

eth0      Interface doesn't support scanning.

---

### Post by kwacka on 2008-01-31
Your need to change your network settings - you're trying to connect on a different channels  and different ESSID.

---

### Post by Pulka on 2008-01-31
already tried auto channel, already tried to put the specific channel, none of those options work. Sometimes, after i try this command : **sudo dhclient wlan0** a few times, i get an ip, but just for a few minutes

---

### Post by kwacka on 2008-01-31
So your card is working and the network is recognised.

Can you connect with something like 'wifi-radar' - available from the universal repository.

Start it from a terminal & note any error messages

---

### Post by Pulka on 2008-01-31
yes, i have wi-fi radar, but i can´t connect throught there also

---

### Post by Pulka on 2008-01-31
it´s always a nightmare to connect wireless with ubuntu. I use in a daily basis 5 diferent computers, and in all of them is a nightmare everytime i install a new desktop

---

### Post by kwacka on 2008-01-31
What are the error messages with wifi-radar? Does it see networks?

The only problem that I've had with wireless (in the last couple of years) has been with a laptop with a internal Broadcom card.

---

### Post by Pulka on 2008-01-31
yes, it shows all the networks available. My card is a D-link.
i don´t know if it matters, but my essid is hidden

---

### Post by kwacka on 2008-01-31
I'm confused that you connect and then it loses the connection, that should rule out encryption problems. What is signal strength like?

Try another channel - maybe interference from other channels, phones, whatever. Also stop wi-fi radar.

---

### Post by Pulka on 2008-01-31
other 4 computers are connected to that network. It´s not the channel.
I already unistalled network manager. Before i had wifi radar, had the same problem

---

### Post by Pulka on 2008-02-01
another day, another failure.
Tried installing ndiswrapper, windows drivers, uninstalling wifi, nothing works.

any ideias?

---

### Post by stalkingwolf on 2008-02-01
try this, it works for me.
System > Administration > Network settings > Connections >  check for wireless connection > 
Hosts >  ff02::ip6 allrouters> add.

I have had great luck establishing connection by doing that.  Then you can fix what needs to be fixed
or not as you choose.

---

### Post by Pulka on 2008-02-01
thanks for the reply, but i already have that host

---

### Post by kwacka on 2008-02-01
You haven't confirmed that you tried the same ESSID for both network & computer - even if they're hidden they must be the same or set to 'any'.. Try 'sudo iwconfig  ra0 essid any' then try connecting (I noticed in your other thread that your connection had changed to ra0 from wlan0 - confirm which it is using iwconfig).

127.0.0.1 is your local computer - if you can't ping that you've **really **got problems.  8)

BTW This is getting old but might be of interest:  [http://ubuntuforums.org/showthread.php?t=176752](http://ubuntuforums.org/showthread.php?t=176752)

---


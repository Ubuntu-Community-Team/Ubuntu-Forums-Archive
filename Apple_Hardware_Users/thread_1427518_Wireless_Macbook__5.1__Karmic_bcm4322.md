---
title: "Wireless Macbook  5.1  Karmic bcm4322"
date: 2010-03-11
forum: Apple Hardware Users
---

### Post by evanuz on 2010-03-11
Hi
I can't stablish a connection
I ve tried with network manager, but it keeps asking the password until i dont provide it.
If i do it manually, i cant get an ip. It just says:

[B]No working leases in persistent database - sleeping.


Some of my info:
[/B]```

wicca@Falcor:~$ lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

``````

wicca@Falcor:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
snd_hda_codec_realtek   210528  1 
decnet                 66476  0 [permanent]
snd_hda_intel          25728  3 
snd_hda_codec          84384  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
snd_pcm_oss            37472  0 
snd_mixer_oss          16220  1 snd_pcm_oss
snd_pcm                76480  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
snd_seq_oss            29216  0 
snd_seq_midi            6656  0 
snd_rawmidi            22336  1 snd_seq_midi
snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi
applesmc               21896  0 
nvidia               8880868  40 
snd_seq                50896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     8636  0 
snd_timer              21540  2 snd_pcm,snd_seq
shpchp                 32272  0 
bcm5974                 8316  0 
uvcvideo               59080  0 
agpgart                34988  1 nvidia
lp                      8964  0 
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               4096  1 applesmc
wl                   1272936  0 
videodev               36736  1 uvcvideo
i2c_nforce2             6784  0 
iptable_filter          3100  0 
btusb                  11856  2 
ip_tables              11692  1 iptable_filter
v4l1_compat            14336  2 uvcvideo,videodev
input_polldev           3716  1 applesmc
snd                    61156  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
x_tables               16544  1 ip_tables
lib80211                6432  2 lib80211_crypt_tkip,wl
mbp_nvidia_bl           2856  0 
snd_page_alloc          9124  2 snd_hda_intel,snd_pcm
joydev                 10240  0 
parport                35340  2 ppdev,lp
hid_apple               6236  0 
usbhid                 38208  0 
forcedeth              54152  0 

``````

wicca@Falcor:~$ sudo lshw -C network
 *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 01
       serial: aa:00:04:00:0a:04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:23 memory:93100000-93103fff



``````

wicca@Falcor:~$ uname -mr
2.6.31-20-generic i686


```

---

### Post by linuxopjemac on 2010-03-12
my experiences with networkmanager are bad. I switched to wicd
```
sudo apt-get install wicd
```
(networkmanager will be automatically removed)

---

### Post by evanuz on 2010-03-12
> **linuxopjemac said:**
> my experiences with networkmanager are bad. I switched to wicd
```
sudo apt-get install wicd
```(networkmanager will be automatically removed)

thanks 
i did it but wicd stucks on obtaining ip address until it says:

Connection Failed: Unable to Get IP Address

---

### Post by linuxopjemac on 2010-03-13
does the router work properly under OSX?

---

### Post by evanuz on 2010-03-14
Yes it does

---

### Post by linuxopjemac on 2010-03-15
I would play a bit with your router settings. I read somewhere that changing from a 13 key password to a 10 key password did the trick for someone. I am not an expert on this, but start from no security to more security and so on...

---


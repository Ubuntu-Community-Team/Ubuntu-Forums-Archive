---
title: "Wireless - The Trials Continue"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by keylime on 2007-08-23
As a newbie to Linux, I decided to install Feisty on a NC4200 rig. So far, it has exceeded expectations, with one glaring exception: I can not get my Intel 2200 chipset to grab a wireless connection. 

I have attempted to read other threads so here is some information:

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:76:10:7C  
          inet addr:172.21.30.40  Bcast:172.21.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:b0ff:fe76:107c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1804641 (1.7 MiB)  TX bytes:391139 (381.9 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:15:00:13:C0:D0  
          inet6 addr: fe80::215:ff:fe13:c0d0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:138 dropped:138 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:16766 (16.3 KiB)
          Interrupt:21 Base address:0x6000 Memory:d8000000-d8000fff 

eth1:avah Link encap:Ethernet  HWaddr 00:15:00:13:C0:D0  
          inet addr:169.254.7.95  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x6000 Memory:d8000000-d8000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89911 (87.8 KiB)  TX bytes:89911 (87.8 KiB)

______________


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"tbstcur"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:118  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

______________________

Any assistance offered will be greatly appreciated; I'm attempting to have this machine function for work purposes (I get to play with this for 3 months - goodie).:)

---

### Post by mikeyphi on 2007-08-23
Is the wireless router 'open' or using limited access? ie only allowing access to listed receivers

Is the router using WEP or other encryption?

---

### Post by keylime on 2007-08-23
There is a WPA key that we use to access the router via a passphrase.

---

### Post by rexy on 2007-08-23
i think it's natively supported so i assume the driver is loaded, you can check with lsmod and lspci.

iwlan wlan0 scanning should return some access points

you can configure it using networkmanager or using wpa_supplicant which is explained [here]("http://ubuntuforums.org/showthread.php?t=202834&highlight=axc111+wpa")

a general howto on wpa in ubuntu can be found [here]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo")

---

### Post by keylime on 2007-08-23
I did the instructions and here's what I got afterwards:

RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 16730
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:15:00:13:c0:d0
Sending on   LPF/eth1/00:15:00:13:c0:d0
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:15:00:13:c0:d0
Sending on   LPF/eth1/00:15:00:13:c0:d0
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
Segmentation fault (core dumped)
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

I am currently on Ethernet so dunno if that caused the failure. Wireless is on.

---

### Post by keylime on 2007-08-23
My network prefs file output is:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid tbstcur
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk ab96328d9b9b55fa150d43404d36b4a9115670a822c38977f05da7dda5575e4f

---

### Post by keylime on 2007-08-23
Module                  Size  Used by
battery                10756  0 
ac                      6020  0 
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
button                  8720  0 
ipw2200               148040  0 
ieee80211              34760  1 ipw2200
tg3                   109700  0 
ndiswrapper           194608  0 
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14208  0 
fat                    53916  1 vfat
usb_storage            72256  0 
libusual               17936  1 usb_storage
arc4                    2944  0 
ecb                     4480  0 
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  0 
snd_rtctimer            4384  0 
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
ppdev                  10116  0 
i915                   24448  3 
drm                    81044  4 i915
speedstep_centrino      9920  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
freq_table              5792  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
asus_acpi              17308  0 
video                  16388  0 
container               5248  0 
dock                   10268  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
af_packet              23816  6 
lp                     12452  0 
fuse                   46612  0 
pcmcia                 39212  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
irtty_sir               9600  0 
sir_dev                17156  1 irtty_sir
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
irda                  201276  2 irtty_sir,sir_dev
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
parport_pc             36388  1 
sdhci                  18700  0 
crc_ccitt               3072  1 irda
tpm_infineon            9112  0 
tpm                    16672  1 tpm_infineon
tpm_bios                8448  1 tpm
joydev                 10816  0 
mmc_core               26756  1 sdhci
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
ieee80211_crypt         7040  2 ieee80211,ieee80211_crypt_wep
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
parport                36936  3 ppdev,lp,parport_pc
hci_usb                18204  0 
bluetooth              55908  5 rfcomm,l2cap,hci_usb
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1               8704  0 
tifm_core              11140  1 tifm_7xx1
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
serio_raw               7940  0 
intel_agp              25244  1 
psmouse                38920  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                35400  3 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
ata_generic             9092  0 
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 usb_storage,sg,sd_mod,libata
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  7 ndiswrapper,usb_storage,libusual,hci_usb,ehci_hcd,uhci_hcd
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by fatdadkev on 2008-02-16
Have you tried 7.10 Gutsy ?

I am typing this on an NC4200 and linked via wireless.

It installed and everything worked fine although I think the only item that might not be working is the auto brightness sensor on the bottom left of the screen.

Wireless does report itself as 2200BG Pro and speed seems fine - although you need to check its turned on (the button on the left side behind the USB port) - even the blue light works ok. If it's not turned on you get the Radio OFF message.

It might be that the previous versions did not detect as good as the new version?

As a side note Compwiz works great as well, 3d cube desktop etc, I've tried Beryl and Emerald as well - they all work fine.

I also set CPU scaling by issuing the command "sudo dpkg-reconfigure gnome-applets" and answering YES to the question (it advises that everyone will be able to set CPU scaling regardless of their security privileges).
This allows you to set the CPU speed on the fly using the taskbar icon at the top, you can lock it into a certain speed or set it to conservative etc.

I hope this helps

---


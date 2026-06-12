---
title: "ASUS K53E Wireless Problem"
date: 2012-04-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jdwbmc on 2012-04-09
I just installed Ubuntu 11.10 32-bit version on an ASUS K53.  Every thing seems to work fine except for the wireless.  I've looked in the forums for a solution and I'm not quite sure what to do.  I've gathered the following information:

John


jdwbmc@Spatha:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Spatha 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

jdwbmc@Spatha:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave Device [1a3b:1186]
	Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c

jdwbmc@Spatha:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp. 

jdwbmc@Spatha:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
      
jdwbmc@Spatha:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no

jdwbmc@Spatha:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
joydev                 17393  0 
asus_nb_wmi            12469  0 
asus_wmi               19333  1 asus_nb_wmi
sparse_keymap          13658  1 asus_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
wmi                    18744  1 asus_wmi
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
i915                  505108  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 112711  0 
psmouse                73673  0 
serio_raw              12990  0 
mac80211              272785  1 ath9k
drm_kms_helper         32889  1 i915
ath9k_common           13599  1 ath9k
drm                   192226  4 i915,drm_kms_helper
ath9k_hw              293893  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
cfg80211              172392  3 ath9k,mac80211,ath
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  3 
libahci                25727  1 ahci
atl1c                  36638  0 
xhci_hcd               72915  0 

jdwbmc@Spatha:/var/lib/NetworkManager$ cat NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

jdwbmc@Spatha:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)

Any help would be appreciated.  Thanks.

John

---

### Post by jdwbmc on 2012-04-11
I just installed Ubuntu 11.10 32-bit version on an ASUS K53. Every thing seems to work fine except for the wireless. I've looked in the forums for a solution and I'm not quite sure what to do. I've gathered the following information:

John


jdwbmc@Spatha:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Spatha 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

jdwbmc@Spatha:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
Subsystem: AzureWave Device [1a3b:1186]
Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
Kernel driver in use: atl1c

jdwbmc@Spatha:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp. 

jdwbmc@Spatha:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSIDff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

jdwbmc@Spatha:~$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
1: asus-wlan: Wireless LAN
Soft blocked: no
Hard blocked: no

jdwbmc@Spatha:~$ lsmod
Module Size Used by
parport_pc 32114 0 
ppdev 12849 0 
snd_hda_codec_hdmi 31426 1 
bnep 17923 2 
rfcomm 38408 0 
bluetooth 148839 10 bnep,rfcomm
snd_hda_codec_realtek 254125 1 
binfmt_misc 17292 1 
joydev 17393 0 
asus_nb_wmi 12469 0 
asus_wmi 19333 1 asus_nb_wmi
sparse_keymap 13658 1 asus_wmi
uvcvideo 67271 0 
videodev 85626 1 uvcvideo
snd_hda_intel 24262 2 
snd_hda_codec 91754 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel
snd_hwdep 13276 1 snd_hda_codec
snd_pcm 80468 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi 13132 0 
wmi 18744 1 asus_wmi
snd_rawmidi 25241 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event
arc4 12473 2 
i915 505108 3 
snd_timer 28932 2 snd_pcm,snd_seq
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k 112711 0 
psmouse 73673 0 
serio_raw 12990 0 
mac80211 272785 1 ath9k
drm_kms_helper 32889 1 i915
ath9k_common 13599 1 ath9k
drm 192226 4 i915,drm_kms_helper
ath9k_hw 293893 2 ath9k,ath9k_common
ath 19387 2 ath9k,ath9k_hw
cfg80211 172392 3 ath9k,mac80211,ath
snd 55902 14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,s nd_seq,snd_timer,snd_seq_device
soundcore 12600 1 snd
snd_page_alloc 14115 2 snd_hda_intel,snd_pcm
mei 36466 0 
i2c_algo_bit 13199 1 i915
video 18908 1 i915
lp 17455 0 
parport 40930 3 parport_pc,ppdev,lp
ahci 21634 3 
libahci 25727 1 ahci
atl1c 36638 0 
xhci_hcd 72915 0 

jdwbmc@Spatha:/var/lib/NetworkManager$ cat NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

jdwbmc@Spatha:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)

Any help would be appreciated. Thanks.

John

---

### Post by praseodym on 2012-04-11
Hi,

your card is "off":
```
wlan0 IEEE 802.11bgn ESSIDff/any
Mode:Managed Access Point: Not-Associated [COLOR="Red"]Tx-Power=0 dBm[/COLOR] 
```
Any button, switch, key or key combination to activate it? Checked the BIOS settings? BIOS reset?

---

### Post by jdwbmc on 2012-04-11
praseodym,

Thanks for the reply.  The only hardware control for turning wifi on and off is the combination of FN-F2 keys.  This works under Windows 7, but not Ubuntu.  At least under Windows, the default seems to be "ON" and wifi works just fine.  It appears that Ubuntu recognizes the card, I'm just not sure what to do to turn it on from a software perspective.  I appreciate any insight, I'm rather new to Ubuntu.  Thanks.

John

---

### Post by jdwbmc on 2012-04-13
It appears the wireless network is disabled.


jdwbmc@Spatha:~$ sudo lshw -C network
[sudo] password for jdwbmc: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 01:08:ca:71:81:10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:de800000-de87ffff memory:de880000-de88ffff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: c8:60:00:29:be:e4
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:52 memory:dd400000-dd43ffff ioport:a000(size=128)

There doesn't appear to be an obvious way to turn on the network.  In Windows the only way is with the keyboard using Fn-F2 combination.  This doesn't work in Ubuntu.  There doesn't appear to be a way either when I look at the BIOS.  What else can I try?  Thanks.

John

---

### Post by jdwbmc on 2012-04-13
It appears the wireless network is disabled.


jdwbmc@Spatha:~$ sudo lshw -C network
[sudo] password for jdwbmc: 
*-network DISABLED 
description: Wireless interface
product: AR9485 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 01
serial: 01:08:ca:71:81:10
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:de800000-de87ffff memory:de880000-de88ffff
*-network
description: Ethernet interface
product: AR8151 v2.0 Gigabit Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: c0
serial: c8:60:00:29:be:e4
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
resources: irq:52 memory:dd400000-dd43ffff ioport:a000(size=12

There doesn't appear to be an obvious way to turn on the network. In Windows the only way is with the keyboard using Fn-F2 combination. This doesn't work in Ubuntu. There doesn't appear to be a way either when I look at the BIOS. What else can I try? Thanks.

John

---

### Post by praseodym on 2012-04-14
Reset the BIOS to default settings.

---

### Post by jdwbmc on 2012-04-14
On the K53, there is no option to reset the BIOS to the default, however, I've gone through all the settings and it appears that they are all at the default settings.  These settings work with Windows 7.  The problem still exists under Ubuntu.

I was wondering if this would be a problem with all versions of Linux.  I went and got a DVD with 5 versions of Linux.  I tried each with the Live version of the system.  There results are as follows:

Ubuntu 11.10 - wireless does not work
Debian 6.0.1 - wireless does not work
Linux Mint 12 - wireless does not work
Fedora 16 - wireless works!
openSUSE 12.1 - wireless works!

It appears that the Debian line of Linux has this problem while others do not.  What is the Debian line doing that is so different that my wireless does not work?

John

---

### Post by jdwbmc on 2012-04-15
I was wondering if this would be a problem with all versions of Linux. I went and got a DVD with 5 versions of Linux. I tried each with the Live version of the system. There results are as follows:

Ubuntu 11.10 - wireless does not work
Debian 6.0.1 - wireless does not work
Linux Mint 12 - wireless does not work
Fedora 16 - wireless works!
openSUSE 12.1 - wireless works!

It appears that the Debian line of Linux has this problem while others do not. What is the Debian line doing that is so different that my wireless does not work?

John

---

### Post by jdwbmc on 2012-04-17
A brief update.  I've tried 3 different things with no success.  Since I'm a novice at this I'm not sure these steps are meaningful, but perhaps add more information.

1)sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

2) sudo ip link set wlan0 up
RTNETLINK answers: Cannot assign requested address

I've also tried editing the /etc/network/interfaces file.
auto wlan0
iface wlan0 inet dhcp
        wireless-essid ANY
        wireless-mode managed

This resulted in the system taking several minutes to boot and finally giving up on configuring the network before finish the start up.

Any other suggestions?

John

---

### Post by jdwbmc on 2012-04-19
At the suggestion of ASUS, I reinstalled the wireless driver.  I was already at the latest version.  This made no difference.  I also upgraded my BIOS from version 217 to version 219.  This also made no difference.  Any other suggestions?

John

---

### Post by jdwbmc on 2012-04-19
At the suggestion of ASUS, I reinstalled the wireless driver. I was already at the latest version. This made no difference. I also upgraded my BIOS from version 217 to version 219. This also made no difference. Any other suggestions?

John

---

### Post by dpharo on 2012-04-21
I have an Asus K53E which I tried Ubuntu 11.10 and the only problem was the wireless. Instead of fighting it I loaded up the Beta version of 12.04 and NO issue with wireless. It worked out of the box!

---

### Post by jdwbmc on 2012-04-21
> **dpharo said:**
> I have an Asus K53E which I tried Ubuntu 11.10 and the only problem was the wireless. Instead of fighting it I loaded up the Beta version of 12.04 and NO issue with wireless. It worked out of the box!

dpharo,

Excellent.  This is the best advice I've had.  I upgraded to 12.04 and the wireless now works.  I'm replying to this message using Ubuntu and my wireless connection.  Thanks!

John

---

### Post by parth.s on 2012-07-12
I have the very same laptop. My issue with wireless is that its connected all the time alright, but most of the times the pages don't load at all, sometimes it gives an dns error, sometimes page not found...

I don't know what to do, i started out with ubuntu 10.04 and tried every stable release till 12.04.. Now I'm trying Fedora too, any ideas? And I have tried re-installing the drivers on the realtek website..

---

### Post by jdwbmc on 2012-07-12
You might try a clean install of 12.04.  I reformatted the partition before doing the install.

John

---

### Post by parth.s on 2012-07-13
I did a clean install each and every time..

---


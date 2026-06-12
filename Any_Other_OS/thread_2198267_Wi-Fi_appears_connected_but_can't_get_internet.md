---
title: "Wi-Fi appears connected but can't get internet"
date: 2014-01-08
forum: Any Other OS
---

### Post by jloowi on 2014-01-08
Hi. I installed Ubuntu 13.10 on an HP Chromebook 14.
I can't get internet, even though Wi-Fi appears to be connected.
I tried running Terminal (using instructions found in similar threads). 
Hoping someone can help me fix it?

I get the following results:

```
user@chrubuntu:~$ lspci -nnk | grep -iA2 net01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1864]
    Kernel driver in use: ath9k
user@chrubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 12d1:1570 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 0cf3:311e Atheros Communications, Inc. 
Bus 002 Device 002: ID 04f2:b40d Chicony Electronics Co., Ltd 
Bus 002 Device 007: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@chrubuntu:~$ lsmod
Module                  Size  Used by
usb_storage            62062  1 
ipt_MASQUERADE         12880  1 
xt_conntrack           12760  1 
ipt_REJECT             12541  2 
xt_tcpudp              12884  4 
iptable_filter         12810  1 
nf_nat_h323            17720  0 
nf_conntrack_h323      73895  1 nf_nat_h323
nf_nat_pptp            13115  0 
nf_nat_proto_gre       13009  1 nf_nat_pptp
nf_conntrack_pptp      19258  1 nf_nat_pptp
nf_conntrack_proto_gre    14434  1 nf_conntrack_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      13121  1 nf_nat_tftp
nf_nat_sip             17152  0 
nf_conntrack_sip       29764  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13518  1 nf_nat_irc
nf_nat_ftp             12770  0 
nf_conntrack_ftp       18638  1 nf_nat_ftp
iptable_nat            13011  1 
nf_conntrack_ipv4      15012  2 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_nat_ipv4            13263  1 iptable_nat
nf_nat                 26711  10 nf_nat_ftp,nf_nat_irc,nf_nat_sip,ipt_MASQUERADE,nf_nat_proto_gre,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,iptable_nat
nf_conntrack           91940  19 nf_nat_ftp,nf_nat_irc,nf_nat_sip,nf_conntrack_proto_gre,ipt_MASQUERADE,nf_nat,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,xt_conntrack,nf_conntrack_ftp,nf_conntrack_irc,nf_conntrack_sip,iptable_nat,nf_conntrack_h323,nf_conntrack_ipv4,nf_conntrack_pptp,nf_conntrack_tftp
ip_tables              27239  2 iptable_filter,iptable_nat
x_tables               34059  6 ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ipt_REJECT
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
crct10dif_pclmul       14289  0 
joydev                 17377  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20359  1 ghash_clmulni_intel
hid_generic            12548  0 
option                 42468  0 
cyapa                  13132  0 
usb_wwan               20380  1 option
usbhid                 53014  0 
usbserial              44667  2 option,usb_wwan
cdc_ether              14351  0 
parport_pc             32701  0 
usbnet                 39525  1 cdc_ether
mii                    13934  1 usbnet
hid                   105858  2 hid_generic,usbhid
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
gpio_ich               13476  0 
rfcomm                 69130  12 
bnep                   19704  2 
snd_hda_codec_realtek    55704  1 
snd_hda_codec_hdmi     41117  1 
chromeos_laptop        14148  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
tpm_infineon           17372  0 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
btusb                  28267  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
bluetooth             372041  22 bnep,btusb,rfcomm
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
arc4                   12608  2 
ath9k                 155779  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
microcode              23576  0 
mac80211              597268  1 ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
serio_raw              13413  0 
i915                  661261  5 
lpc_ich                21080  0 
cfg80211              480503  3 ath,ath9k,mac80211
drm_kms_helper         52710  1 i915
tpm_tis                19123  0 
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   297056  4 i915,drm_kms_helper
video                  19318  1 i915
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
i2c_designware_pci     13135  0 
i2c_designware_core    14768  1 i2c_designware_pci
ahci                   25819  3 
libahci                31928  1 ahci
user@chrubuntu:~$ iwconfig
usb0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"6929"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: F6:7E:11:D1:7B:57   
          Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
user@chrubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Thanks in advance!

---

### Post by Bucky Ball on 2014-01-08
You installed Chrubuntu or Ubuntu??? In your terminal it gives the impression you are using Chrubuntu ...

In the meantime, post the output of:

```
sudo lshw -C network
```

---

### Post by jloowi on 2014-01-08
Hi, thanks for the quick reply.

I installed Chrubuntu - ubuntu-desktop (default, based on [these instructions by the developer]("http://chromeos-cr48.blogspot.ca/2013/10/chrubuntu-for-new-chromebooks-now-with.html")).

Is it normal if the command **sudo lshw -C network**&#8203; returns 'command not found' ?

---

### Post by Bucky Ball on 2014-01-08
*Thread moved to **Other OS/Distro Support**.*

Chrubuntu is not officially support in the main support areas of the forum.

> **jloowi said:**
> 

Is it normal if the command **sudo lshw -C network**&#8203; returns 'command not found' ?

No, but this might be something not used in Chrubuntu. Don't know, but doubt that's the case. Strange.

Have you tried plugging in with an ethernet cable and doing updates? You could then check Additional Drivers, but again, no idea whether that exists in Chrubuntu. Might pay to post on the Chrubuntu forum as well if they have one.

---

### Post by jloowi on 2014-01-08
My problem is that the HP Chromebook 14 doesn't have an Ethernet port - Wi-Fi and Bluetooth are the only connectivity I have, so I can't get additional drivers (as you suggest).

I will try to post in the Chrubuntu Google+ community, and report back if I find a solution (in case someone else has the problem as well).

---

### Post by Bucky Ball on 2014-01-08
> **Bucky Ball said:**
> Have you tried plugging in with an ethernet cable and doing updates? You could then check Additional Drivers ...

? Give that a go. Additional Drivers, or something like it (Hardware Drivers?) should be there somewhere. Many fixes for wireless will require you to be online with a cable in any case. ;)

---

### Post by jloowi on 2014-01-08
HP Chromebook 14 doesn't have an Ethernet port. :(

---

### Post by mark65ak on 2014-01-08
try the ifconfig command rather than iwconfig.  It should show better info like if the adapter is up, ip addresses, packets, collitions etc.

---

### Post by jloowi on 2014-01-08
Thanks mark65ak,

Here's what I got with ifconfig rather than iwconfig

```
user@chrubuntu:~$ lspci -nnk | grep -iA2 net01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1864]
	Kernel driver in use: ath9k
user@chrubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 12d1:1570 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 0cf3:311e Atheros Communications, Inc. 
Bus 002 Device 002: ID 04f2:b40d Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
user@chrubuntu:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12880  1 
xt_conntrack           12760  1 
ipt_REJECT             12541  2 
xt_tcpudp              12884  4 
iptable_filter         12810  1 
nf_nat_h323            17720  0 
nf_conntrack_h323      73895  1 nf_nat_h323
nf_nat_pptp            13115  0 
nf_nat_proto_gre       13009  1 nf_nat_pptp
nf_conntrack_pptp      19258  1 nf_nat_pptp
nf_conntrack_proto_gre    14434  1 nf_conntrack_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      13121  1 nf_nat_tftp
nf_nat_sip             17152  0 
nf_conntrack_sip       29764  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13518  1 nf_nat_irc
nf_nat_ftp             12770  0 
nf_conntrack_ftp       18638  1 nf_nat_ftp
iptable_nat            13011  1 
nf_conntrack_ipv4      15012  2 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_nat_ipv4            13263  1 iptable_nat
nf_nat                 26711  10 nf_nat_ftp,nf_nat_irc,nf_nat_sip,ipt_MASQUERADE,nf_nat_proto_gre,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,iptable_nat
nf_conntrack           91940  19 nf_nat_ftp,nf_nat_irc,nf_nat_sip,nf_conntrack_proto_gre,ipt_MASQUERADE,nf_nat,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,xt_conntrack,nf_conntrack_ftp,nf_conntrack_irc,nf_conntrack_sip,iptable_nat,nf_conntrack_h323,nf_conntrack_ipv4,nf_conntrack_pptp,nf_conntrack_tftp
ip_tables              27239  2 iptable_filter,iptable_nat
x_tables               34059  6 ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ipt_REJECT
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
joydev                 17377  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20359  1 ghash_clmulni_intel
option                 42468  0 
usb_wwan               20380  1 option
usbserial              44667  2 option,usb_wwan
cdc_ether              14351  0 
usbnet                 39525  1 cdc_ether
mii                    13934  1 usbnet
cyapa                  13132  0 
gpio_ich               13476  0 
btusb                  28267  0 
snd_hda_codec_realtek    55704  1 
parport_pc             32701  0 
ppdev                  17671  0 
snd_hda_codec_hdmi     41117  1 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
chromeos_laptop        14148  0 
bnep                   19704  2 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
videobuf2_memops       13362  1 videobuf2_vmalloc
rfcomm                 69130  12 
microcode              23576  0 
videobuf2_core         40499  1 uvcvideo
snd_seq_midi           13324  0 
bluetooth             372041  22 bnep,btusb,rfcomm
tpm_infineon           17372  0 
videodev              133509  2 uvcvideo,videobuf2_core
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
arc4                   12608  2 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
ath9k                 155779  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
serio_raw              13413  0 
mac80211              597268  1 ath9k
lpc_ich                21080  0 
cfg80211              480503  3 ath,ath9k,mac80211
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_designware_pci     13135  0 
i2c_designware_core    14768  1 i2c_designware_pci
soundcore              12680  1 snd
tpm_tis                19123  0 
i915                  661261  5 
video                  19318  1 i915
drm_kms_helper         52710  1 i915
mac_hid                13205  0 
drm                   297056  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
ahci                   25819  1 
libahci                31928  1 ahci
```

```
user@chrubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


usb0      Link encap:Ethernet  HWaddr 02:2c:80:13:92:63  
          inet6 addr: fe80::2c:80ff:fe13:9263/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4645 (4.6 KB)


wlan0     Link encap:Ethernet  HWaddr 48:5a:b6:11:4e:0b  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5a:b6ff:fe11:4e0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10480 (10.4 KB)
```

```
user@chrubuntu:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

---

### Post by jloowi on 2014-01-11
So I tried a different install using Crouton (which lets you switch OS instantly), instead of Chrubuntu. Wi-Fi worked. I re-installed Chrubuntu and even tried running Elementary OS; it looks like Wi-Fi is unable to connect without Chrome OS running alongside it.

---


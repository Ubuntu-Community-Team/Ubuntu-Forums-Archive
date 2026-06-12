---
title: "AOD257 wifi not working"
date: 2011-08-19
forum: Any Other OS
---

### Post by zensawa on 2011-08-19
Hi, Having trouble getting my wifi to connect. The wifi icon keeps  spinning and spinning even after typing all information correct.

Information:

AOD257
Mint Linux 11(also tried ubuntu 10.04, and 11.04) (using mint atm)

uname -a

Linux lap-AOD257 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

lsmod

Module Size Used by
binfmt_misc 13213 1
sha256_generic 20911 2
cryptd 19801 0
aes_i586 16956 238
aes_generic 38023 1 aes_i586
parport_pc 32111 0
ppdev 12849 0
dm_crypt 22463 1
snd_hda_codec_realtek 255820 1
snd_hda_intel 24140 2
snd_hda_codec 90901 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13274 1 snd_hda_codec
snd_pcm 80244 2 snd_hda_intel,snd_hda_codec
joydev 17322 0
snd_seq_midi 13132 0
arc4 12473 2
snd_rawmidi 25269 1 snd_seq_midi
sparse_keymap 13666 0
ath9k 103633 0
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event
mac80211 257001 1 ath9k
snd_timer 28659 2 snd_pcm,snd_seq
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq
ipt_REJECT 12512 1
ipt_LOG 12784 5
uvcvideo 66851 0
xt_limit 12541 7
xt_tcpudp 12531 8
ipt_addrtype 12535 4
xt_state 12514 7
ath9k_common 13611 1 ath9k
ath9k_hw 300328 2 ath9k,ath9k_common
snd 55295 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev 75143 1 uvcvideo
ath 19141 2 ath9k,ath9k_hw
cfg80211 156212 3 ath9k,mac80211,ath
psmouse 73312 0
ip6table_filter 12711 1
rts_pstor 348243 0
ip6_tables 22545 1 ip6table_filter
serio_raw 12990 0
nf_nat_irc 12542 0
nf_conntrack_irc 13138 1 nf_nat_irc
nf_nat_ftp 12548 0
nf_nat 24827 2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4 19024 9 nf_nat
nf_defrag_ipv4 12649 1 nf_conntrack_ipv4
nf_conntrack_ftp 13106 1 nf_nat_ftp
nf_conntrack 69744 7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter 12706 1
ip_tables 18125 1 iptable_filter
x_tables  21907 10  ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
soundcore 12600 1 snd
snd_page_alloc 14073 2 snd_hda_intel,snd_pcm
lp 13349 0
parport 36746 3 parport_pc,ppdev,lp
dm_raid45 88410 0
xor 21860 1 dm_raid45
btrfs 527341 0
zlib_deflate 26594 1 btrfs
libcrc32c 12543 1 btrfs
i915 450944 3
drm_kms_helper 40745 1 i915
drm 180037 4 i915,drm_kms_helper
ahci 21591 2
r8169 42534 0
libahci 25548 1 ahci
i2c_algo_bit 13184 1 i915
video 18951 1 i915


Any help would be much appreciated, Thanks

---

### Post by zensawa on 2011-08-19
Forgot to post this:



 I. scanning WIFI PCI devices...
  -- Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
      ==> PCI ID = 168c:002b (rev 01)
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vboxnet0  no wireless extensions.

-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:40:63:7c  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9a:8fff:fe40:637c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98338431 (98.3 MB)  TX bytes:3480110 (3.4 MB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9375 (9.3 KB)  TX bytes:9375 (9.3 KB)

wlan0     Link encap:Ethernet  HWaddr cc:af:78:1d:b6:19  
          inet6 addr: fe80::ceaf:78ff:fe1d:b619/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:678 (678.0 B)  TX bytes:930 (930.0 B)

-------------------------
* V. querying DHCP...
-------------------------
* VI. querying nslookup google.com...
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.113.104
Name:	google.com
Address: 74.125.113.105
Name:	google.com
Address: 74.125.113.106
Name:	google.com
Address: 74.125.113.147
Name:	google.com
Address: 74.125.113.99
Name:	google.com
Address: 74.125.113.103

---

### Post by zensawa on 2011-08-19
Motivational bump, this did nothing

	sudo modprobe ath9k

---

### Post by Perfect Storm on 2011-08-19
Moved to Other OS/Distro Talk.


Please don't bump your thread so often. There's an edit button.

---


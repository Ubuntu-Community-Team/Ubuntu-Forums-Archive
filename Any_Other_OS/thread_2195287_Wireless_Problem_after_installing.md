---
title: "Wireless Problem after installing"
date: 2013-12-23
forum: Any Other OS
---

### Post by kcs.ieor on 2013-12-23
hi all, I was using Ubuntu. It was not connecting to wireless. So, I switched to Linux Mint.

During installation of Mint 16 the wireless connection seemed not to be a  problem. My network was found and i got the connection.
But after reboot, the connection to WLAN does't work.

I tried seeking a solution on Linux mint forums but no luck. So, hope to get a solution here.


_**cat /etc/lsb-release; uname -a**_

```

leader@leader ~ $ cat /etc/lsb-release; uname -a
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=16
DISTRIB_CODENAME=petra
DISTRIB_DESCRIPTION="Linux Mint 16 Petra"
Linux leader 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux

```

[U]**lspci -nnk | grep -iA2 net **
```

Code: [Select all]("http://forums.linuxmint.com/viewtopic.php?f=53&t=151561#")leader@leader ~ $ lspci -nnk | grep -iA2 net
05:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 02)
   Subsystem: Acer Incorporated [ALI] Device [1025:013e]
   Kernel driver in use: r8169
leader@leader ~ $ lsusb
Bus 002 Device 006: ID 0000:0538  
Bus 002 Device 010: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 002 Device 005: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 002 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a117 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

**_rfkill list all_**[/U]

```

leader@leader ~ $ rfkill list all
0: acer-bluetooth: Bluetooth
   Soft blocked: yes
   Hard blocked: no
leader@leader ~ $ lsmod
Module                  Size  Used by
ext2                   63128  1 
nls_iso8859_1          12617  1 
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87192  2 hid_generic,usbhid
coretemp               13195  0 
snd_hda_codec_hdmi     40508  1 
snd_hda_codec_realtek    45473  1 
snd_hda_intel          42658  3 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
microcode              18830  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
nvidia               8503438  42 
psmouse                90642  0 
serio_raw              13189  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
lpc_ich                16864  0 
videodev              107508  2 uvcvideo,videobuf2_core
snd                     60790  17  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
jmb38x_ms              18222  0 
memstick               16008  1 jmb38x_ms
drm                   242354  2 nvidia
soundcore              12600  1 snd
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18893  2 
bluetooth             323534  10 bnep,rfcomm
binfmt_misc            13140  1 
dm_multipath           22402  0 
scsi_dh                14458  1 dm_multipath
joydev                 17097  0 
ir_lirc_codec          12869  0 
lirc_dev               19324  1 ir_lirc_codec
ir_mce_kbd_decoder     13030  0 
ir_sony_decoder        12625  0 
ir_sanyo_decoder       12727  0 
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ir_rc6_decoder         12754  0 
ir_nec_decoder         12787  0 
ir_jvc_decoder         12655  0 
ir_rc5_decoder         12622  0 
rc_rc6_mce             12454  0 
mxm_wmi                12893  0 
ene_ir                 28067  0 
rc_core                 26398  11  ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,ene_ir,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
wmi                    18590  2 acer_wmi,mxm_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
dm_mirror              21715  0 
dm_region_hash         15984  1 dm_mirror
dm_log                 18072  2 dm_region_hash,dm_mirror
usb_storage            48294  1 
ahci                   25579  3 
libahci                26554  1 ahci
sdhci_pci              18481  0 
r8169                  61434  0 
sdhci                  37468  1 sdhci_pci
mii                    13654  1 r8169
video                  18777  1 acer_wmi

```

[B][U]inxi -Nn
[/U][/B]```

Code: [Select all]("http://forums.linuxmint.com/viewtopic.php?f=53&t=151561#")leader@leader ~ $ inxi -Nn
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 00:1e:ec:c8:24:02

```


Please help..

---

### Post by bapoumba on 2013-12-23
Moved to Other OS/Distro Support.

---

### Post by buzzingrobot on 2013-12-23
The info you listed doesn't show a wifi card, just the ethernet card.

If you have access to an ethernet connection to the net, check Mint's Driver Manager and see if it offers a driver for your wireless card.

For example, inxi -Nn here shows this:```


Card-1: Intel Centrino Ultimate-N 6300 driver: iwlwifi 
IF: wlan0 state: down mac: 3c:a9:f4:56:ba:04
Card-2: Intel 82579LM Gigabit Network Connection driver: e1000e 
IF: eth0 state: up speed: 1000 Mbps duplex: full mac: 3c:97:0e:b7:c3:4e


```

---

### Post by kcs.ieor on 2013-12-24
Mint's driver manager shows in attachment. 
Please advise, what should I do..
[ATTACH=CONFIG]248862[/ATTACH]

---

### Post by buzzingrobot on 2013-12-24
> **kcs.ieor said:**
> Mint's driver manager shows in attachment. 
Please advise, what should I do..
[ATTACH=CONFIG]248862[/ATTACH]

It's found the video card and listed the available drivers.  It isn't listing a wireless driver which means it can't find the wireless card or it did find the wireless card and has no driver to offer. 

The network manager applet is in your panel and working?  Ditto the network panel in Settings (Cinnamon) or the equivalent in Mate? That's where wireless is typically enabled.

---

### Post by kcs.ieor on 2013-12-25
network manager applet is in panel.. and it did not show wireless. 
But suddenly on Christmas eve.. wirelss is working..  it is the same case with others too.. 
Please see the post that I made in linux mint forums.. [http://forums.linuxmint.com/viewtopic.php?f=53&t=151561&p=800342#p800342](http://forums.linuxmint.com/viewtopic.php?f=53&t=151561&p=800342#p800342)
Now confused... what to do?

---


---
title: "cannot connect to detected wireless networks - Ubuntu 10.04 - G4 Powerbook"
date: 2011-05-05
forum: Apple Hardware Users
---

### Post by clarissa.w on 2011-05-05
Hi there

I have a G4 550Mhz powerbook (Titanium Onyx) which I have installed Ubuntu 10.04. The powerbook detects wifi networks but cannot connect to them. I have searched the forums and I installed b43-fwcutter which downloaded a file from the internet and installed it but I still cannot connect to the wireless networks.

_Output of terminal using lspci and ifconfig commands_ before installing b43-fwcutter

```
clarissa@ubuntu-ppc:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:24:0e.0 FireWire (IEEE 1394): Agere Systems FW322/323
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)
clarissa@ubuntu-ppc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:93:45:25:8c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:30:65:08:72:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:57 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3584 (3.5 KB)  TX bytes:3584 (3.5 KB)
```I then installed b43-fwcutter.

_Output of terminal using lspci and ifconfig commands af__ter installing b43-fwcutter_

```
clarissa@ubuntu-ppc:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:24:0e.0 FireWire (IEEE 1394): Agere Systems FW322/323
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)
clarissa@ubuntu-ppc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:93:45:25:8c  
          inet6 addr: fe80::203:93ff:fe45:258c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2347 (2.3 KB)  TX bytes:5421 (5.4 KB)
          Interrupt:41 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:30:65:08:72:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:57 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:820 (820.0 B)  TX bytes:820 (820.0 B)
```

---

### Post by clarissa.w on 2011-05-05
I think I must have an original Airport card according to an existing thread. ([http://ubuntuforums.org/showthread.php?t=1590569&highlight=orinoco+PPC+airport](http://ubuntuforums.org/showthread.php?t=1590569&highlight=orinoco+PPC+airport))

[http://ubuntuforums.org/showpost.php?p=10445087&postcount=6](http://ubuntuforums.org/showpost.php?p=10445087&postcount=6)
> [COLOR=#000000][FONT=Arial][FONT=Verdana]I see in the wireless thread
[http://ubuntuforums.org/showthread.p...41#post9957641]("http://ubuntuforums.org/showthread.php?p=9957641#post9957641") 
an [COLOR=#FF0000]**orinoco**[/COLOR] module. That points to a classic [COLOR=#FF0000]**Airport**[/COLOR] instead of Broadcom.
You might want to install linux-firmware-nonfree, that's the package in MintPPC that provides firmware for older [COLOR=#FF0000]**airport**[/COLOR] models. This will give you:

Agere/Prism/Symbol [COLOR=#FF0000]**Orinoco**[/COLOR] firmware (STA mode), version 9.48 Hermes I (agere_sta_fw.bin)


All [COLOR=#FF0000]**airport**[/COLOR] cards work out of the box nowadays in MintPPC...

You also need to have the latest firmware from Apple for this card (9.52).[/FONT][/FONT][/COLOR]_Output of commands lsmod, lspci -nn and lspci -vnn | grep 14e4 on my powerbook_

```
clarissa@ubuntu-ppc:~$ lsmod
Module                  Size  Used by
rfcomm                 43737  4 
sco                    10661  2 
bridge                 58038  0 
stp                     2244  1 bridge
bnep                   12779  2 
l2cap                  37132  16 rfcomm,bnep
btusb                  13403  2 
bluetooth              64147  9 rfcomm,sco,bnep,l2cap,btusb
binfmt_misc             8530  1 
ppdev                   7877  0 
lp                      9304  0 
parport                39110  2 ppdev,lp
uinput                  8693  2 
radeon                806358  0 
ttm                    62502  1 radeon
drm_kms_helper         31243  1 radeon
drm                   192322  3 radeon,ttm,drm_kms_helper
cpufreq_stats           4202  0 
ipv6                  300187  10 
snd_powermac           68187  1 
snd_aoa_i2sbus         20791  0 
snd_pcm_oss            47872  0 
loop                   16940  0 
snd_mixer_oss          19382  1 snd_pcm_oss
apm_emu                 1468  0 
apm_emulation           7311  2 apm_emu
snd_pcm                87159  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
michael_mic             2384  4 
snd_page_alloc          7660  1 snd_pcm
snd_seq_dummy           1766  0 
snd_seq_oss            36288  0 
snd_seq_midi            6161  0 
snd_rawmidi            24746  1 snd_seq_midi
snd_seq_midi_event      7367  2 snd_seq_oss,snd_seq_midi
snd_seq                61897  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24515  2 snd_pcm,snd_seq
snd_seq_device          7524  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
airport                 3786  0 
pcmcia                 37678  0 
snd                    70636  12 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           25736  2 
orinoco                71915  1 airport
soundcore               7534  1 snd
rsrc_nonstatic         11098  1 yenta_socket
pmac_zilog             18110  0 
cfg80211              152905  1 orinoco
uninorth_agp            8437  1 
serial_core            23813  1 pmac_zilog
evdev                  10257  27 
snd_aoa_soundbus        4916  1 snd_aoa_i2sbus
rfkill                 20725  4 bluetooth,cfg80211
pcmcia_core            40156  3 pcmcia,yenta_socket,rsrc_nonstatic
rtc_generic             1391  0 
agpgart                39895  3 ttm,drm,uninorth_agp
usbhid                 44246  0 
ohci1394               35584  0 
sungem                 32704  0 
hid                    78556  1 usbhid
sungem_phy             12365  1 sungem
ieee1394               97330  1 ohci1394
windfarm_core          10420  0 
clarissa@ubuntu-ppc:~$ lspci -nn
0000:00:0b.0 Host bridge [0600]: Apple Computer Inc. UniNorth 1.5 AGP [106b:002d]
0000:00:10.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
0001:10:0b.0 Host bridge [0600]: Apple Computer Inc. UniNorth 1.5 PCI [106b:002e]
0001:10:17.0 Class [ff00]: Apple Computer Inc. KeyLargo Mac I/O [106b:0022] (rev 03)
0001:10:18.0 USB Controller [0c03]: Apple Computer Inc. KeyLargo USB [106b:0019]
0001:10:19.0 USB Controller [0c03]: Apple Computer Inc. KeyLargo USB [106b:0019]
0001:10:1a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
0001:11:00.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
0001:11:00.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
0001:11:00.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 02)
0002:24:0b.0 Host bridge [0600]: Apple Computer Inc. UniNorth 1.5 Internal PCI [106b:002f]
0002:24:0e.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811]
0002:24:0f.0 Ethernet controller [0200]: Apple Computer Inc. UniNorth GMAC (Sun GEM) [106b:0021] (rev 01)
clarissa@ubuntu-ppc:~$ lspci -vnn | grep 14e4
clarissa@ubuntu-ppc:~$ 
```How do I find if I have the latest firmwave? I will do a google search to find out.

Can anyone confirm that installing ```
linux-firmware-nonfree
```  fixes the problem for Ubuntu 10.04 as per the comment from the thread?

Thanks

---

### Post by linuxopjemac on 2011-05-06
That is correct.

---


---
title: "[SOLVED] Broadcom Wireless Driver for Penryn Macbook Pro"
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by jbiggs12 on 2008-11-07
Help!
I have a Penryn MacBook Pro, and I'm dual-booting Ubuntu and Mac OS X 10.5. I've looked at previous posts, and since I'm extremely new to linux, and have no terminal skills whatsoever, it all looks like gibberish to me. Can someone tell me, in complete idiot speak, how I get my broadcom wifi chip to work? I've seen people have relative success (i.e., a slow, but working internet connection), and I don't care if it's slow or not, I just don't want to boot back up into OSX just to google something. Thanks!


(by the way, I've attached the official linux driver file from Broadcom. Where to I extract the tarball file to?)

---

### Post by _alex_ on 2008-11-07
Hello jbiggs12,

The boradcom driver is included in Ubuntu Hardy (with the latest updates) and Intrepid. All you need to do is enable it in System > Administration > Hardware Drivers.

We also have a wiki page that may be useful to you: [https://help.ubuntu.com/community/MacBookPro_Penryn](https://help.ubuntu.com/community/MacBookPro_Penryn)

Cheers,
Alex

---

### Post by jbiggs12 on 2008-11-07
I'm running Intrepid, but when I try to enable the driver (even with a LAN connection) it stays at 0% when installing the file, then the install window spontaneously disappears, and the driver says it's enabled. However, my system tray shows no wireless option. Do I have to manually put my wireless connection icon into my tray, or is there something wrong?

---

### Post by cyberdork33 on 2008-11-07
can you post the output of:

"lsmod"

and

"ifconfig"

---

### Post by jbiggs12 on 2008-11-07
lsmod:
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  4 
binfmt_misc            16904  1 
sco                    18308  2 
rfcomm                 44432  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  16 rfcomm,bnep
uinput                 15744  2 
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
joydev                 18368  0 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
uvcvideo               62728  0 
snd_seq_oss            38528  0 
compat_ioctl32          9344  1 uvcvideo
snd_seq_midi           14336  0 
appleir                12544  0 
usbhid                 35840  0 
videodev               41344  1 uvcvideo
hid                    50560  1 usbhid
btusb                  19736  3 
v4l1_compat            22404  2 uvcvideo,videodev
bcm5974                16000  0 
evdev                  17696  14 
bluetooth              61924  11 sco,rfcomm,bnep,l2cap,btusb
ieee80211_crypt_tkip    17024  0 
nvidia               6900560  38 
snd_rawmidi            29824  1 snd_seq_midi
wl                   1076372  0 
pcspkr                 10624  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
i2c_core               31892  1 nvidia
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                     12292  0 
iTCO_wdt               18596  0 
battery                18436  0 
video                  25104  4 
intel_agp              33724  0 
output                 11008  1 video
soundcore              15328  1 snd
iTCO_vendor_support    11652  1 iTCO_wdt
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
agpgart                42184  2 nvidia,intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_piix               24580  1 
ata_generic            12932  0 
libata                177312  3 pata_acpi,ata_piix,ata_generic
ohci1394               37936  0 
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
sky2                   53380  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  8 uvcvideo,appleir,usbhid,btusb,bcm5974,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:22:41:1e:e2:74  
          inet addr:10.0.1.11  Bcast:10.0.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:429 errors:0 dropped:1 overruns:0 frame:1
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:207328 (207.3 KB)  TX bytes:28686 (28.6 KB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:1f:5b:d0:73:d4  
          inet6 addr: fe80::21f:5bff:fed0:73d4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:2456
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

---

### Post by cyberdork33 on 2008-11-07
You have the wl driver enabled (which is the same as the Broadcom Proprietary Driver that you posted the tarball for) and the device is showing as eth2 in the output of ifconfig which means that the driver is "working". 

Can you make sure that the network-manager applet is not showing anything for wifi?

PS you should use the [noparse]```
code tags
```[/noparse] when posting terminal output and such. It makes things a lot easier to read.

---

### Post by jbiggs12 on 2008-11-07
yes! that did it! thank you very much.

now if only I could get my sound working.......

---

### Post by cyberdork33 on 2008-11-07
Ok, well I didn't really get you to do anything other than check that the module was loaded.

If you feel this topic is now solved, please mark it as solved from the threads tools menu at the top of the page.


P.S.
For sound, make sure your channels are all turned up and unmuted in 'alsamixer'.

If that doesn't do it for you, you might need to do this:
[https://help.ubuntu.com/community/MacBookPro_SantaRosa#Change%203:%20Sound](https://help.ubuntu.com/community/MacBookPro_SantaRosa#Change%203:%20Sound)

---


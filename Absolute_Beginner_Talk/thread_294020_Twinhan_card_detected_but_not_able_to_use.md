---
title: "Twinhan card detected but not able to use"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by ttremeth on 2006-11-06
[http://www.linuxtv.org/wiki/index.php/TwinhanDTV_Digital_Terrestrial_TV_Card_Ter](http://www.linuxtv.org/wiki/index.php/TwinhanDTV_Digital_Terrestrial_TV_Card_Ter)



Oct 31 19:47:41 desktop kernel: [   55.725676] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Oct 31 19:47:41 desktop kernel: [   55.872308] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Oct 31 20:48:43 desktop kernel: [   55.204819] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Oct 31 20:48:43 desktop kernel: [   55.660998] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  1 12:23:03 desktop kernel: [   56.931254] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  1 12:23:03 desktop kernel: [   57.110437] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  1 16:50:19 desktop kernel: [   54.727434] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  1 16:50:19 desktop kernel: [   54.771219] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  1 18:26:49 desktop kernel: [   55.391105] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  1 18:26:49 desktop kernel: [   55.572767] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  1 21:16:37 desktop kernel: [   50.560707] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  1 21:16:37 desktop kernel: [   51.345431] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  2 22:00:48 desktop kernel: [   48.430167] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  2 22:00:48 desktop kernel: [   48.861806] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  3 07:15:29 desktop kernel: [   55.911348] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  3 07:15:29 desktop kernel: [   56.201707] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  3 18:05:57 desktop kernel: [   49.646267] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  3 18:05:57 desktop kernel: [   49.924778] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  3 21:58:02 desktop kernel: [   49.852293] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  3 21:58:02 desktop kernel: [   50.490835] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  3 23:26:08 desktop kernel: [   60.209619] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  3 23:26:08 desktop kernel: [   60.797333] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  4 08:43:39 desktop kernel: [   59.682740] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  4 08:43:39 desktop kernel: [   59.805377] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  4 22:41:01 desktop kernel: [   55.950766] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  4 22:41:01 desktop kernel: [   56.658521] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  5 21:09:45 desktop kernel: [   55.217290] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  5 21:09:45 desktop kernel: [   55.406525] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Nov  6 18:02:18 desktop kernel: [   55.852683] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Nov  6 18:02:18 desktop kernel: [   56.177769] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.


 56.177715] bt878: AUDIO driver version 0.0.0 loaded
[   56.177747] bt878: Bt878 AUDIO function found (0).
[   56.177763] ACPI: PCI Interrupt 0000:01:08.1[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 74
[   56.177769] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[   56.177776] bt878(0): Bt878 (rev 17) at 01:08.1, irq: 74, latency: 32, memory: 0xfdffe000

---

### Post by ttremeth on 2006-11-06
terry@desktop:~$ lsmod
Module                  Size  Used by
nls_utf8                3840  1 
ntfs                  109128  1 
binfmt_misc            16012  1 
rfcomm                 51360  0 
l2cap                  31744  5 rfcomm
bluetooth              64644  4 rfcomm,l2cap
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  1 cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  0 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sony_acpi               7704  0 
sbs                    20928  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
hotkey                 14536  0 
dev_acpi               17540  0 
container               6656  0 
button                  9888  0 
battery                14088  0 
asus_acpi              21924  0 
ac                      8328  0 
ipv6                  334432  17 
snd_bt87x              20516  0 
dvb_bt8xx              21124  0 
nxt6000                10372  1 dvb_bt8xx
mt352                   9988  1 dvb_bt8xx
dvb_pll                15748  1 dvb_bt8xx
sp887x                 10628  1 dvb_bt8xx
dst_ca                 16384  1 dvb_bt8xx
dst                    28036  2 dvb_bt8xx,dst_ca
dvb_core              103088  2 dvb_bt8xx,dst_ca
cx24110                11780  1 dvb_bt8xx
or51211                12676  1 dvb_bt8xx
zl10353                 8324  1 dvb_bt8xx
lgdt330x               11420  1 dvb_bt8xx
sbp2                   29448  0 
lp                     16584  0 
af_packet              29452  2 
bt878                  14824  2 dvb_bt8xx,dst
tsdev                  11136  0 
snd_intel8x0           42024  1 
snd_ac97_codec        127064  1 snd_intel8x0
snd_ac97_bus            4352  1 snd_ac97_codec
snd_pcm_oss            57344  0 
snd_pcm               108168  4 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          22784  2 snd_pcm_oss
snd_seq_dummy           6020  0 
snd_seq_oss            45824  0 
tuner                  62764  0 
nvidia               5444468  12 
usblp                  18176  0 
usb_storage            89792  1 
bttv                  222196  2 dvb_bt8xx,bt878
snd_seq_midi           12160  0 
snd_rawmidi            34432  1 snd_seq_midi
snd_seq_midi_event     11520  2 snd_seq_oss,snd_seq_midi
snd_seq                77344  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video_buf              33156  1 bttv
ir_common              31876  1 bttv
libusual               21544  1 usb_storage
compat_ioctl32         11264  1 bttv
i2c_algo_bit           11784  1 bttv
usbhid                 51360  0 
sg                     44584  0 
snd_timer              31112  2 snd_pcm,snd_seq
snd_seq_device         12180  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            20352  3 tuner,bttv,compat_ioctl32
btcx_risc               7304  1 bttv
tveeprom               20112  1 bttv
i2c_nforce2             9984  0 
videodev               14208  1 bttv
rt2500                229096  1 
floppy                 76648  0 
snd                    79016  11 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14112  2 snd
snd_page_alloc         13200  3 snd_bt87x,snd_intel8x0,snd_pcm
parport_pc             43560  1 
parport                49932  2 lp,parport_pc
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
i2c_core               29312  16 i2c_ec,dvb_bt8xx,nxt6000,mt352,sp887x,dst,cx24110,or51211,zl10353,lgdt330x,tuner,nvidia,bttv,i2c_algo_bit,tveeprom,i2c_nforce2
evdev                  14592  3 
pcspkr                  5248  0 
ext3                  164624  1 
jbd                    74024  1 ext3
forcedeth              37644  0 
ohci1394               40776  0 
ieee1394              387704  2 sbp2,ohci1394
ehci_hcd               40456  0 
ohci_hcd               25988  0 
usbcore               167840  7 usblp,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
ide_generic             2944  0 
ide_disk               21248  3 
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
generic                 7428  0 
amd74xx                17712  0 [permanent]
sd_mod                 25728  2 
sata_nv                13572  0 
libata                 88984  1 sata_nv
scsi_mod              181424  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                19472  0 
processor              38280  1 thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit
terry@desktop:~$  modprobe
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
terry@desktop:~$ sudo modprobe bttv
terry@desktop:~$ sudo modprobe bt878
terry@desktop:~$ sudo modprobe dvb_core
terry@desktop:~$ sudo modprobe dst
terry@desktop:~$ sudo modprobe dvb-bt8xx
terry@desktop:~$ modeprobe dst
bash: modeprobe: command not found
terry@desktop:~$ modprobe dst
terry@desktop:~$ lsmod
Module                  Size  Used by
nls_utf8                3840  1 
ntfs                  109128  1 
binfmt_misc            16012  1 
rfcomm                 51360  0 
l2cap                  31744  5 rfcomm
bluetooth              64644  4 rfcomm,l2cap
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  1 cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  0 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sony_acpi               7704  0 
sbs                    20928  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
hotkey                 14536  0 
dev_acpi               17540  0 
container               6656  0 
button                  9888  0 
battery                14088  0 
asus_acpi              21924  0 
ac                      8328  0 
ipv6                  334432  17 
snd_bt87x              20516  0 
dvb_bt8xx              21124  0 
nxt6000                10372  1 dvb_bt8xx
mt352                   9988  1 dvb_bt8xx
dvb_pll                15748  1 dvb_bt8xx
sp887x                 10628  1 dvb_bt8xx
dst_ca                 16384  1 dvb_bt8xx
dst                    28036  2 dvb_bt8xx,dst_ca
dvb_core              103088  2 dvb_bt8xx,dst_ca
cx24110                11780  1 dvb_bt8xx
or51211                12676  1 dvb_bt8xx
zl10353                 8324  1 dvb_bt8xx
lgdt330x               11420  1 dvb_bt8xx
sbp2                   29448  0 
lp                     16584  0 
af_packet              29452  2 
bt878                  14824  2 dvb_bt8xx,dst
tsdev                  11136  0 
snd_intel8x0           42024  1 
snd_ac97_codec        127064  1 snd_intel8x0
snd_ac97_bus            4352  1 snd_ac97_codec
snd_pcm_oss            57344  0 
snd_pcm               108168  4 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          22784  2 snd_pcm_oss
snd_seq_dummy           6020  0 
snd_seq_oss            45824  0 
tuner                  62764  0 
nvidia               5444468  12 
usblp                  18176  0 
usb_storage            89792  1 
bttv                  222196  2 dvb_bt8xx,bt878
snd_seq_midi           12160  0 
snd_rawmidi            34432  1 snd_seq_midi
snd_seq_midi_event     11520  2 snd_seq_oss,snd_seq_midi
snd_seq                77344  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video_buf              33156  1 bttv
ir_common              31876  1 bttv
libusual               21544  1 usb_storage
compat_ioctl32         11264  1 bttv
i2c_algo_bit           11784  1 bttv
usbhid                 51360  0 
sg                     44584  0 
snd_timer              31112  2 snd_pcm,snd_seq
snd_seq_device         12180  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            20352  3 tuner,bttv,compat_ioctl32
btcx_risc               7304  1 bttv
tveeprom               20112  1 bttv
i2c_nforce2             9984  0 
videodev               14208  1 bttv
rt2500                229096  1 
floppy                 76648  0 
snd                    79016  11 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14112  2 snd
snd_page_alloc         13200  3 snd_bt87x,snd_intel8x0,snd_pcm
parport_pc             43560  1 
parport                49932  2 lp,parport_pc
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
i2c_core               29312  16 i2c_ec,dvb_bt8xx,nxt6000,mt352,sp887x,dst,cx24110,or51211,zl10353,lgdt330x,tuner,nvidia,bttv,i2c_algo_bit,tveeprom,i2c_nforce2
evdev                  14592  3 
pcspkr                  5248  0 
ext3                  164624  1 
jbd                    74024  1 ext3
forcedeth              37644  0 
ohci1394               40776  0 
ieee1394              387704  2 sbp2,ohci1394
ehci_hcd               40456  0 
ohci_hcd               25988  0 
usbcore               167840  7 usblp,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
ide_generic             2944  0 
ide_disk               21248  3 
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
generic                 7428  0 
amd74xx                17712  0 [permanent]
sd_mod                 25728  2 
sata_nv                13572  0 
libata                 88984  1 sata_nv
scsi_mod              181424  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                19472  0 
processor              38280  1 thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit


BUT no /dev/dvb/adapter0/ directory

WHY WHY I am going freken insane!!!!

---

### Post by ttremeth on 2006-11-06
bump again, checked [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB) all looks ok but no  /dev/dvb/adapter0/ firmware in place.

---

### Post by ttremeth on 2006-11-06
bump

---

### Post by ttremeth on 2006-11-06
bump

---

### Post by blendmaster on 2006-11-06
How about [here]("http://www.mythtv.org/wiki/index.php/Twinhan_Mini_Ter_Ubuntu_Breezy_Install")?

I haven't tried it (no tv card myself), but that's what I've heard referred to on the threads.

It's a little outdated (actually, a lot), but maybe you could try it and see where you go.

---

### Post by ttremeth on 2006-11-06
Thanks for that! I did have a look but my card is detected fine by edgy. I am hoping all those line above will be obvious to someone.

---

### Post by ttremeth on 2006-11-07
erry@desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

lsmod | grep bt8xx - just a blank line

---

### Post by Lem on 2006-11-07
Adding the following to /etc/modules worked for me.

dvb-bt8xx
dst
dvb_core

then restart.

---

### Post by ttremeth on 2006-11-08
yesp worked, will test for sound etc

---

### Post by Lem on 2006-11-08
Working now?

I built a fresh edgy box yesterday for mythtv and all I needed to get my twinhan dvb card recognised was add the modules as I stated above.

---

### Post by filrad on 2006-11-08
I have a twinhan 1022 perfectly working under winzoz and that was perfectly working under Ubuntu Dapper as well. Since I upgraded to Edgy (with a completely new installation) it does not work anymore. As suggested I added the lines

dvb-bt8xx 
dst
dvb_core

in /etc/modules  (I tried also to put bttv)


and 

options dvb_core dvb_shutdown_timeout=0
options bttv i2c_hw=1 card=0x71

in /etc/modprobe.d/options .


My "dmesg | grep bt8" says

[17179591.196000] bt878: AUDIO driver version 0.0.0 loaded
[17179591.196000] bt878: Bt878 AUDIO function found (0).
[17179591.196000] bt878_probe: card id=[0x1fefe], Unknown card.
[17179591.196000] bt878: probe of 0000:00:0a.1 failed with error -22
[17179593.272000] dvb_bt8xx: unable to determine DMA core of card 0,
[17179593.272000] dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try removing it.
[17179593.272000] dvb-bt8xx: probe of dvb0 failed with error -14


I don't know what I should do... Thanks, Filippo

---

### Post by Lem on 2006-11-09
Have you tried removing or hashing out the line;

options bttv i2c_hw=1 card=0x71

?

I didn't have to specify the card ID. It should probe ok without it.

---

### Post by Lem on 2006-11-09
PS.. no need to add bttv - already loaded.

---

### Post by filrad on 2006-11-09
Have you tried removing or hashing out the line;

options bttv i2c_hw=1 card=0x71

?

I didn't have to specify the card ID. It should probe ok without it.



Without this line the system hangs after rebooting.

---

### Post by filrad on 2006-11-09
SOLVED!!!!!!

The problem was the eeprom of my dvb card


check this page

[http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A](http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A)

probably you can solve your problem as well

---

### Post by pfred on 2007-03-13
I have a similar problem with my Twinhan DVB-T 3021 (a.k.a. Visionplus). The modules below doesn't load and I have no /dev/dvb/adapter0/, not even /dev/dvb/. When I add the following:

> **Lem said:**
> Adding the following to /etc/modules worked for me.

dvb-bt8xx
dst
dvb_core

then restart.

...my computer freezes at bootup. I also tried to modprobe the modules:
> modprobe dst
modprobe dvb_core
modprobe dvb-bt8xx


The first two lines work fine but when I press enter after "modprobe dvb-bt8xx" my computer totally freezes and both the mouse and keyboard stops responding, hence I have to reboot.

dmesg | grep bt says:
> 
~$ dmesg | grep bt
[17179589.236000] bttv: driver version 0.9.16 loaded
[17179589.236000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179589.412000] bttv: Bt8xx card found (0).
[17179589.412000] bttv0: Bt878 (rev 17) at 0000:02:08.0, irq: 217, latency: 32, mmio: 0xe7000000
[17179589.412000] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[17179589.412000] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[17179589.412000] bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
[17179589.412000] bttv0: using tuner=4
[17179589.428000] bttv0: add subdevice "dvb0"
[17179589.428000] bt878: AUDIO driver version 0.0.0 loaded
[17179589.428000] bt878: Bt878 AUDIO function found (0).
[17179589.428000] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[17179589.428000] bt878(0): Bt878 (rev 17) at 02:08.1, irq: 217, latency: 32, memory: 0xe7001000

...which all seems to be in order.

lsmod | grep bt says:
> ~$ lsmod | grep bt
bt878                  12472  0 
bttv                  176116  1 bt878
video_buf              27652  1 bttv
ir_common              28548  1 bttv
compat_ioctl32          2432  1 bttv
i2c_algo_bit           10376  1 bttv
v4l2_common            17280  2 tuner,bttv
btcx_risc               6280  1 bttv
tveeprom               16144  1 bttv
videodev               10752  1 bttv
i2c_core               23424  7 i2c_ec,nvidia,tuner,bttv,i2c_algo_bit,tveeprom,i2c_nforce2


...which is also fine. 
I am very confused on why the module "dvb-bt8xx" causes the computer to crash. I haven't been able to find anyone with the same problem on the forum. If anyone has a solution or can point me in the right direction... please help.

---

### Post by pfred on 2007-03-27
bump!!

---

### Post by jmore9 on 2007-07-09
Hello
I have the twinhan visionplus 3250 atsc tuner card installed and seen by kaffeine and klear.   But i cannot use it because both apps are requiring me to provide a channels.conf.  I tried using dvb utils scan but was not able to save the results from the tuner scan which worked perfectly as far as i could tell.  Anyone know how to save the atsc output from the scan ?

---


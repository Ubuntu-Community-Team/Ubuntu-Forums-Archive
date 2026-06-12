---
title: "playing avi"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-01-28
i turn on the comptuer and theres no volume, now this has happened plenty of times and i fixed it thanks to the help here! but now i have no sound at all and cant play mp3s or avis i get i message as seen in the screenshot. please help i use my comp for all my media (i dont own a stereo a tv or a dvd player) in cluding cable. thanks in advance!!!

---

### Post by antgul3382 on 2007-01-28
oops heres that screenshot!@

---

### Post by taurus on 2007-01-28
Do you hear any sound when you log in to Gnome?

---

### Post by antgul3382 on 2007-01-28
no sound at all

---

### Post by taurus on 2007-01-28
Do you have one of those onboard integrated soundcards?  What's the output of this command from a terminal?

```
lsmod
```

---

### Post by antgul3382 on 2007-01-28
whatever this means here ya go thanks!

> Module                  Size  Used by
isofs                  36792  1 
udf                    87684  0 
binfmt_misc            11784  1 
rfcomm                 38936  0 
l2cap                  23300  5 rfcomm
bluetooth              48996  4 rfcomm,l2cap
vmnet                  38444  13 
vmmon                 115948  0 
sg                     35356  0 
sd_mod                 21648  2 
ipv6                  257632  8 
powernow_k8            10888  0 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  1 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
af_packet              21768  2 
nls_utf8                2304  2 
nls_cp437               6016  2 
vfat                   13440  2 
fat                    54556  1 vfat
lp                     11972  0 
tsdev                   8256  0 
snd_intel8x0           33436  1 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
saa7134_alsa           13856  0 
nvidia               6827412  22 
snd_pcm_oss            46080  0 
snd_pcm                80520  4 snd_intel8x0,snd_ac97_codec,saa7134_alsa,snd_pcm_oss
snd_mixer_oss          18560  1 snd_pcm_oss
snd_seq_dummy           4100  0 
snd_seq_oss            34304  0 
usb_storage            73408  1 
scsi_mod              141320  3 sg,sd_mod,usb_storage
i2c_ali1535             7044  0 
libusual               15632  1 usb_storage
tuner                  53804  0 
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
i2c_ali1563             7556  0 
i2c_ali15x3             7812  0 
snd_seq_midi            9088  0 
snd_rawmidi            25600  1 snd_seq_midi
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23172  2 snd_pcm,snd_seq
saa7134               116704  1 saa7134_alsa
video_buf              26372  2 saa7134_alsa,saa7134
compat_ioctl32          1536  1 saa7134
v4l2_common            16384  2 tuner,saa7134
v4l1_compat            14212  1 saa7134
ir_kbd_i2c              8976  1 saa7134
ir_common              27652  2 saa7134,ir_kbd_i2c
i2c_core               22288  8 i2c_ec,nvidia,i2c_ali1535,tuner,i2c_ali1563,i2c_ali15x3,saa7134,ir_kbd_i2c
snd_seq_device          8972  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
8139cp                 22528  0 
8139too                27136  0 
mii                     6016  2 8139cp,8139too
snd                    55428  13 snd_intel8x0,snd_ac97_codec,saa7134_alsa,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev                9728  1 saa7134
soundcore               9952  1 snd
pcspkr                  3072  0 
analog                 11680  0 
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
psmouse                40072  0 
serio_raw               7300  0 
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
gameport               15368  1 analog
ali_agp                 7424  0 
amd64_agp              12228  1 
evdev                  10496  2 
agpgart                33456  3 nvidia,ali_agp,amd64_agp
rtc                    12596  0 
ext3                  138632  1 
jbd                    55700  1 ext3
ehci_hcd               32520  0 
ohci_hcd               20740  0 
usbcore               130304  5 usb_storage,libusual,ehci_hcd,ohci_hcd
ide_generic             1536  0 
ide_cd                 32416  1 
cdrom                  37792  1 ide_cd
ide_disk               17664  4 
generic                 5252  0 
alim15x3               12428  0 [permanent]
thermal                14600  0 
processor              26028  2 powernow_k8,thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability


---

### Post by taurus on 2007-01-28
Looks like you have some sound modules loaded.  What is your soundcard anyway?

```
lspci
```

---

### Post by antgul3382 on 2007-01-28
its a onboard realtek ac97 job  > 00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


---

### Post by taurus on 2007-01-28
Do you see your soundcard on System -> Preferences -> Sound -> Sounds -> Default sound card: (from the drop down menu)?

---

### Post by antgul3382 on 2007-01-28
o but i changed it and it works now! thanksz! why would it just switch like that i know i didnt change it and two night ago it worked fine????

---

### Post by taurus on 2007-01-28
Who knows why it switched.  I just know how to fix it!  :wink:

---


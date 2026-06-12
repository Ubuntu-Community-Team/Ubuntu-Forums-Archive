---
title: "Sound works/doesn't work on each startup"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by thadiusdean on 2007-02-24
Let me clarify. I boot up my computer, and the sound works fine. I get the startup music, audio works fine, all is dandy (well, not *all* but that's for another thread.) However, I may turn off my computer and come back the next day only to have all audio dissapear! As far as I can tell this is completely random.

Here is some info:

In sound preferences:
All three Sound Playback options are set to Autodetect while the Sound Capture option is set to ALSA. None of the tests work. My default sound card is NVidia CK804. Tell me if you would like me to list my other sound cards. 

Any help is appreciated. :)

---

### Post by n8bounds on 2007-02-25
umm..you mean you have MORE than one sound card in that PC?

---

### Post by tgalati4 on 2007-02-25
Go into your BIOS, shut off PnP operating system, turn off serial ports, usb, and parallel port. (This is temporary.)  See if sound works consistently.

Linux sometimes has issues assigning proper interrupts to devices on-the-fly.  Plug-N-Play was supposed to solve this in Windows and it works for the most part.  In Linux, you have to be more specific about assignments.

post the following:

lspci
more /proc/interrupts
aplay -l
lsmod

Once you get it set up correctly, it tends to work reliably.

Keep the faith.

---

### Post by thadiusdean on 2007-02-25
> **n8bounds said:**
> umm..you mean you have MORE than one sound card in that PC?
Yeah... I have CA0106, NVidia CK804, MPU-401 UART, and USB Audio if my headphones are turned on.
> **tgalati4 said:**
> Go into your BIOS, shut off PnP operating system, turn off serial ports, usb, and parallel port. (This is temporary.)  See if sound works consistently.

Linux sometimes has issues assigning proper interrupts to devices on-the-fly.  Plug-N-Play was supposed to solve this in Windows and it works for the most part.  In Linux, you have to be more specific about assignments.

post the following:

lspci
more /proc/interrupts
aplay -l
lsmod

Once you get it set up correctly, it tends to work reliably.

Keep the faith.

I can't mess around with my BIOS right now (and I'm not sure if I'm able to actually do all that you listed but I'll try,) but here are my outputs:

lspci
```
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
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Secondary)
05:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:08.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

more /proc/interrupts
```
           CPU0       
  0:     999087    IO-APIC-edge  timer
  1:        773    IO-APIC-edge  i8042
  7:          1    IO-APIC-edge  parport0
  8:          3    IO-APIC-edge  rtc
  9:          0   IO-APIC-level  acpi
 10:          0    IO-APIC-edge  MPU401 UART
 12:      20268    IO-APIC-edge  i8042
 50:          0   IO-APIC-level  ohci_hcd:usb1
 58:      55351   IO-APIC-level  ehci_hcd:usb2
 66:          3   IO-APIC-level  ohci1394
 74:         46   IO-APIC-level  skge, snd_ca0106
 82:     600484   IO-APIC-level  eth1, radeon@pci:0000:01:00.0
217:      15467   IO-APIC-level  libata
225:     120693   IO-APIC-level  libata, NVidia CK804
233:          0   IO-APIC-level  libata
NMI:          0 
LOC:     998940 
ERR:          0
MIS:          0

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lsmod
```
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  2 
drm                    74644  3 radeon
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
ipv6                  272288  8 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  2 
nls_utf8                3200  1 
ntfs                  112116  1 
agpgart                34888  1 drm
sbp2                   24584  0 
lp                     12964  0 
usblp                  15488  0 
tsdev                   9152  0 
snd_mpu401              9640  0 
snd_mpu401_uart        10240  1 snd_mpu401
sg                     37404  0 
snd_intel8x0           34844  1 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
snd_ca0106             36228  0 
snd_rawmidi            27264  2 snd_mpu401_uart,snd_ca0106
snd_seq_device          9868  1 snd_rawmidi
snd_ac97_codec         97696  2 snd_intel8x0,snd_ca0106
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_intel8x0,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd_ac97_bus            3456  1 snd_ac97_codec
8139too                29056  0 
floppy                 63044  0 
skge                   40336  0 
pcspkr                  4352  0 
snd_page_alloc         11400  3 snd_intel8x0,snd_ca0106,snd_pcm
snd                    58372  13 snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ca0106,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
mii                     6912  1 8139too
psmouse                41352  0 
serio_raw               8452  0 
evdev                  11392  1 
analog                 12960  0 
i2c_nforce2             8192  0 
gameport               17160  1 analog
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
i2c_core               23424  2 i2c_ec,i2c_nforce2
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142856  2 
jbd                    62228  1 ext3
usb_storage            75072  0 
libusual               17040  1 usb_storage
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
forcedeth              32268  0 
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  6 usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
ide_generic             2432  0 
sata_sil               11016  0 
generic                 6276  0 
sd_mod                 22656  5 
amd74xx                15260  0 [permanent]
sata_nv                11268  4 
libata                 74892  2 sata_sil,sata_nv
scsi_mod              144648  6 sbp2,sg,sr_mod,usb_storage,sd_mod,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

Sorry for the late reply.

EDIT: If it helps at all, sound was *not* working when I entered those commands.
EDIT: Nevermind, my speakers were off. Sound's working fine. :P

---

### Post by tgalati4 on 2007-02-25
You have what is called an "Edge" case.  You are operating on the outer limits of what a PC is able to do.  There may not be enough interrupts to drive all of the sound cards.  Windows drivers interact directly with the hardware and sometimes you get better performance and or compatibility with multiple sound cards.

Linux uses modules inserted into the kernel.  These interact with pre-compiled hooks to intereact with the hardware.  Based on lspci you have a lot of stuff going on.

There are a few things you can do to get better performance.  First I would blacklist ipv6--you don't need it for now.  You can search blacklist in the forums on how to do this.

You can also recompile the kernel to incorporate some of these modules and that may gain you a performance increase as well as a hard-coded interrupt assignment.

Normally a PC is hardpressed to operated two sound cards because each card has A/D converters, DSP, sythesizer, joystick control, etc, and each of these gobble up the limited interrupts and I/0 ports available.  

You can disable the second IDE channel, the floppy drive, and suspend/hibernate mode--this will free up more interrupts.  It's not ideal, but it may be enough to get you going.

This setup is beyond my expertise as far as configuration.  Some other sound guru needs to chime in.

I would experiment with Dyne:bolic.  It's a live CD that is compiled as a realtime kernel which guarantees 95% of your CPU cycles going to sound functions.  It's optimized for multimedia.  See if that works with all of your hardware.

When in normal desktop mode, I would blacklist sound modules that you really don't need so the rest of the system can operate at 100%

I can't say with confidence that if all of your hardware works 100% in Windows that you can get it working 100% in Linux because I am not aware of the interaction between all of the sound modules.

If you explore the Jack audio server (on Dyne:bolic) you can do some crazy patchwork digitally that is truly impressive.  Check it out.

Good luck.

---

### Post by thadiusdean on 2007-02-26
Wow, thanks for the amazing reply tgalati4!

---

### Post by tgalati4 on 2007-02-26
Keep us posted on what works and what doesn't.  You're not the only one struggling to get sound to work properly.

---


---
title: "Webcam help please...."
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-03-08
I bought a USB Genuis EYE 110, I know I should have read about this and made sure it worked before buying but i didnt. I have never configured a cam in ubuntu (or any other distro) so I need some help. So far the only thing I did was install v4l-conf and when i went to my graphics menu and clicked it my screen turned black, and second time white (have to reboot both times with the reset button).

Ant tips, links for advice would be awesome!

thanks for your time and have a good weekend!!

:)

---

### Post by PriceChild on 2008-03-08
Please type 'lsusb' in a terminal and paste the output here.

---

### Post by rockinlinux on 2008-03-08
sorry, should have said...it shows on my usb

home@home-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 093a:2472 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

---

### Post by kwacka on 2008-03-08
searching for the id 093a:2472 tells us that this needs the gspca driver.

Check the output of 'lsmod' to check that this module is loaded, if not use synaptic to install the sources & take it from there.

See if 'camorama' gives you an image.

---

### Post by rockinlinux on 2008-03-08
here is my lsmod, not sure what im looking for here:

home@home-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12936  1 
fglrx                1547660  27 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vboxdrv                60720  0 
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  4 
cpufreq_userspace       5280  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
video                  18060  0 
ac                      6148  0 
dock                   10656  0 
sbs                    19592  0 
button                  8976  0 
container               5504  0 
battery                11012  0 
coretemp                8448  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  2 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
serio_raw               8068  0 
intel_agp              25620  0 
agpgart                35016  2 fglrx,intel_agp
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ipv6                  273892  14 
pcspkr                  4224  0 
ext3                  133896  3 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  5 
ata_generic             8452  0 
pata_marvell            8064  0 
ata_piix               17540  5 
libata                125168  3 ata_generic,pata_marvell,ata_piix
r8169                  32260  0 
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


About the camorama. it says "cannot connect to video device (/dev/video0)"

---

### Post by rockinlinux on 2008-03-09
ok I installed the gspca-source and installed it using synaptic. I still do not see the gspca on my lsmod. Also I still get the same error say it cant find my camera.

lsmod after the isntall and reboot:
home@home-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12936  1 
fglrx                1547660  27 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vboxdrv                60720  0 
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  4 
cpufreq_userspace       5280  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
video                  18060  0 
ac                      6148  0 
dock                   10656  0 
sbs                    19592  0 
button                  8976  0 
container               5504  0 
battery                11012  0 
coretemp                8448  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipv6                  273892  14 
serio_raw               8068  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  0 
agpgart                35016  2 fglrx,intel_agp
psmouse                39952  0 
evdev                  11136  3 
pcspkr                  4224  0 
ext3                  133896  3 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  5 
ata_generic             8452  0 
pata_marvell            8064  0 
ata_piix               17540  5 
ehci_hcd               36492  0 
r8169                  32260  0 
uhci_hcd               26640  0 
libata                125168  3 ata_generic,pata_marvell,ata_piix
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by PriceChild on 2008-03-09
Try```
sudo modprobe gspca
```then see if camorama works.

---

### Post by rockinlinux on 2008-03-09
same message :(

---

### Post by rockinlinux on 2008-03-11
anyone else have any ideas???

thanks :)

---

### Post by rockinlinux on 2008-03-11
here is something that might help.

When look in /dev there is no video0

---

### Post by intel on 2008-03-11
after you plugin the webcam, do 
#modprobe gspca
then post the output of 
#dmesg

---

### Post by gecko113 on 2008-03-11
well i dunno if i'm much help to you but i have an xps m1530 and my web cam wasn't working. so i fooled around with the settings of it in Ekiga softphone and i manged to get it to work. best advice fool around with the settings and it should come to. Good luck :)

---

### Post by SLA_leandrin on 2008-03-11
OK, same problem down here.
I have already compiled the gspca driver, and it's loaded on the kernell.

$ lsusb

```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 093a:2472 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

$ lsmod
```
Module                  Size  Used by
gspca                 608336  0 
videodev               29312  1 gspca
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev
snd_rtctimer            4384  0 
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19592  0 
battery                11012  0 
ac                      6148  0 
container               5504  0 
dock                   10656  0 
button                  8976  0 
video                  18060  11 
ndiswrapper           192924  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  76 
serio_raw               8068  0 
pcspkr                  4224  0 
psmouse                39952  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
agpgart                35016  1 nvidia
k8temp                  6656  0 
i2c_nforce2             7040  0 
i2c_core               26112  2 nvidia,i2c_nforce2
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
sata_nv                20612  4 
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
forcedeth              51592  0 
ehci_hcd               36492  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
ohci_hcd               22916  0 
usbcore               138632  5 gspca,ndiswrapper,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
capability              5896  0 
commoncap               8320  1 capability
fuse                   47124  5 

```

$ dmesg
```
[ 2009.664000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01). Trying to recover by ending request.
[ 2408.852000] Linux video capture interface: v2.00
[ 2408.920000] usbcore: registered new interface driver gspca
[ 2408.920000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[ 2815.840000] usb 1-2: USB disconnect, address 5
[ 3013.796000] usb 1-2: new full speed USB device using ohci_hcd and address 6
[ 3014.008000] usb 1-2: configuration #1 chosen from 1 choice
[ 3532.364000] usb 1-2: USB disconnect, address 6
[ 3556.308000] usb 1-2: new full speed USB device using ohci_hcd and address 7
[ 3556.520000] usb 1-2: configuration #1 chosen from 1 choice

```

If i run Camorama i get a message of error:

```
Could not connect to video device (/dev/video0)
Please check connection
```


$ camorama -D
```
VIDIOCGCAP  --  could not get camera capabilities, exiting.....
```


I don't know what to do next.
Thanks in advance for any tip.

Leandro.

---

### Post by rockinlinux on 2008-03-13
ok i did:

```
 # modprobe gspca
```

here is the dmesg:

```
   [   25.180748] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   25.181267] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   25.181282] SMP alternatives: switching to SMP code
[   25.181335] Booting processor 2/2 eip 3000
[   25.191517] Initializing CPU#2
[   25.268562] Calibrating delay using timer specific routine.. 6011.77 BogoMIPS (lpj=12023554)
[   25.268566] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   25.268569] monitor/mwait feature present.
[   25.268571] CPU: L1 I cache: 32K, L1 D cache: 32K
[   25.268572] CPU: L2 cache: 4096K
[   25.268573] CPU: Physical Processor ID: 0
[   25.268574] CPU: Processor Core ID: 2
[   25.268575] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   25.269024] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   25.269032] SMP alternatives: switching to SMP code
[   25.269041] Booting processor 3/3 eip 3000
[   25.279223] Initializing CPU#3
[   25.356389] Calibrating delay using timer specific routine.. 6011.77 BogoMIPS (lpj=12023550)
[   25.356393] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   25.356396] monitor/mwait feature present.
[   25.356398] CPU: L1 I cache: 32K, L1 D cache: 32K
[   25.356399] CPU: L2 cache: 4096K
[   25.356400] CPU: Physical Processor ID: 0
[   25.356401] CPU: Processor Core ID: 3
[   25.356402] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   25.356866] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   25.356878] Total of 4 processors activated (24050.84 BogoMIPS).
[   25.357010] ENABLING IO-APIC IRQs
[   25.357162] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.504157] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   25.524141] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   25.544131] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   25.564102] Brought up 4 CPUs
[   25.894831] migration_cost=13,3667
[   25.894932] Booting paravirtualized kernel on bare hardware
[   25.894976] Time:  7:21:52  Date: 02/13/108
[   25.894989] NET: Registered protocol family 16
[   25.895038] EISA bus registered
[   25.895041] ACPI: bus type pci registered
[   25.895145] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   25.895146] PCI: Using configuration type 1
[   25.895147] Setting up standard PCI resources
[   25.898006] ACPI: EC: Look up EC in DSDT
[   25.900553] ACPI: Interpreter enabled
[   25.900554] ACPI: (supports S0 S1 S3 S4 S5)
[   25.900564] ACPI: Using IOAPIC for interrupt routing
[   25.900658] Error attaching device data
[   25.900679] Error attaching device data
[   25.900702] Error attaching device data
[   25.900724] Error attaching device data
[   25.904621] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.904634] PCI: Probing PCI hardware (bus 00)
[   25.905693] PCI: Transparent bridge - 0000:00:1e.0
[   25.905736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.905820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   25.905893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   25.905944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   25.905993] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   25.907792] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[   25.907863] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[   25.907931] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 *14 15)
[   25.908000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[   25.908069] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[   25.908139] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[   25.908207] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[   25.908276] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[   25.908336] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.908341] pnp: PnP ACPI init
[   25.908345] ACPI: bus type pnp registered
[   25.910213] pnp: PnP ACPI: found 17 devices
[   25.910215] ACPI: ACPI bus type pnp unregistered
[   25.910217] PnPBIOS: Disabled by ACPI PNP
[   25.910241] PCI: Using ACPI for IRQ routing
[   25.910243] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.919443] NET: Registered protocol family 8
[   25.919445] NET: Registered protocol family 20
[   25.919471] pnp: 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   25.919476] pnp: 00:0a: ioport range 0xa00-0xadf has been reserved
[   25.919478] pnp: 00:0a: ioport range 0xae0-0xaef has been reserved
[   25.919481] pnp: 00:0b: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   25.919482] pnp: 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[   25.919485] pnp: 00:0d: iomem range 0xffc00000-0xffefffff could not be reserved
[   25.919488] pnp: 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
[   25.919490] pnp: 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   25.919492] pnp: 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[   25.919495] pnp: 00:10: iomem range 0x0-0x9ffff could not be reserved
[   25.919497] pnp: 00:10: iomem range 0xc0000-0xcffff could not be reserved
[   25.919498] pnp: 00:10: iomem range 0xe0000-0xfffff could not be reserved
[   25.919500] pnp: 00:10: iomem range 0x100000-0x7fffffff could not be reserved
[   25.923286] Time: tsc clocksource has been installed.
[   25.949596] PCI: Bridge: 0000:00:01.0
[   25.949598]   IO window: c000-cfff
[   25.949600]   MEM window: fe800000-fe8fffff
[   25.949602]   PREFETCH window: d0000000-dfffffff
[   25.949604] PCI: Bridge: 0000:00:1c.0
[   25.949605]   IO window: disabled.
[   25.949608]   MEM window: disabled.
[   25.949610]   PREFETCH window: disabled.
[   25.949613] PCI: Bridge: 0000:00:1c.4
[   25.949614]   IO window: d000-dfff
[   25.949617]   MEM window: fe900000-fe9fffff
[   25.949620]   PREFETCH window: disabled.
[   25.949623] PCI: Bridge: 0000:00:1c.5
[   25.949624]   IO window: e000-efff
[   25.949627]   MEM window: fea00000-feafffff
[   25.949630]   PREFETCH window: disabled.
[   25.949633] PCI: Bridge: 0000:00:1e.0
[   25.949633]   IO window: disabled.
[   25.949636]   MEM window: feb00000-febfffff
[   25.949639]   PREFETCH window: disabled.
[   25.949647] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.949651] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.949662] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   25.949665] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   25.949677] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   25.949680] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   25.949691] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   25.949694] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   25.949701] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.949707] NET: Registered protocol family 2
[   25.987173] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.987202] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   25.987587] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.987722] TCP: Hash tables configured (established 131072 bind 65536)
[   25.987723] TCP reno registered
[   25.999215] checking if image is initramfs... it is
[   26.358650] Freeing initrd memory: 7065k freed
[   26.359167] audit: initializing netlink socket (disabled)
[   26.359175] audit(1205392911.960:1): initialized
[   26.359242] highmem bounce pool size: 64 pages
[   26.360434] VFS: Disk quotas dquot_6.5.1
[   26.360462] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.360510] io scheduler noop registered
[   26.360511] io scheduler anticipatory registered
[   26.360512] io scheduler deadline registered
[   26.360520] io scheduler cfq registered (default)
[   26.360616] Boot video device is 0000:01:00.0
[   26.360664] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.360685] assign_interrupt_mode Found MSI capability
[   26.360686] Allocate Port Service[0000:00:01.0:pcie00]
[   26.360732] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.360760] assign_interrupt_mode Found MSI capability
[   26.360761] Allocate Port Service[0000:00:1c.0:pcie00]
[   26.360781] Allocate Port Service[0000:00:1c.0:pcie02]
[   26.360833] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   26.360861] assign_interrupt_mode Found MSI capability
[   26.360862] Allocate Port Service[0000:00:1c.4:pcie00]
[   26.360881] Allocate Port Service[0000:00:1c.4:pcie02]
[   26.360933] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   26.360961] assign_interrupt_mode Found MSI capability
[   26.360962] Allocate Port Service[0000:00:1c.5:pcie00]
[   26.360982] Allocate Port Service[0000:00:1c.5:pcie02]
[   26.361069] isapnp: Scanning for PnP cards...
[   26.446314] Switched to high resolution mode on CPU 1
[   26.446330] Switched to high resolution mode on CPU 2
[   26.446353] Switched to high resolution mode on CPU 3
[   26.450245] Switched to high resolution mode on CPU 0
[   26.713124] isapnp: No Plug & Play device found
[   26.725700] Real Time Clock Driver v1.12ac
[   26.725767] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.725842] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.726177] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.726618] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.726688] input: Macintosh mouse button emulation as /class/input/input0
[   26.726737] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   26.728778] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.728781] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.728865] mice: PS/2 mouse device common for all mice
[   26.728929] EISA: Probing bus 0 at eisa.0
[   26.728951] EISA: Detected 0 cards.
[   26.729020] TCP cubic registered
[   26.729030] NET: Registered protocol family 1
[   26.729045] Using IPI No-Shortcut mode
[   26.729158]   Magic number: 0:520:369
[   26.729395] Freeing unused kernel memory: 364k freed
[   26.746414] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.833460] AppArmor: AppArmor initialized<5>audit(1205392913.460:2):  type=1505 info="AppArmor initialized" pid=1260
[   27.836630] fuse init (API version 7.8)
[   27.839682] Failure registering capabilities with primary security module.
[   27.867706] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  AD, should be A4 [20070126]
[   27.867714] ACPI: SSDT 7FFC00E0, 0277 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[   27.867961] ACPI: SSDT 7FFC0570, 0277 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[   27.868177] ACPI: SSDT 7FFC0A00, 0277 (r1 DpgPmm  P003Ist       12 INTL 20051117)
[   27.868391] ACPI: SSDT 7FFC0E90, 0277 (r1 DpgPmm  P004Ist       12 INTL 20051117)
[   28.086020] usbcore: registered new interface driver usbfs
[   28.086034] usbcore: registered new interface driver hub
[   28.086047] usbcore: registered new device driver usb
[   28.086451] USB Universal Host Controller Interface driver v3.0
[   28.086491] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.086498] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   28.086500] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   28.086572] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   28.086593] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
[   28.086652] usb usb1: configuration #1 chosen from 1 choice
[   28.086666] hub 1-0:1.0: USB hub found
[   28.086668] hub 1-0:1.0: 2 ports detected
[   28.116021] SCSI subsystem initialized
[   28.128778] libata version 2.21 loaded.
[   28.130471] Floppy drive(s): fd0 is 1.44M
[   28.146343] FDC 0 is a post-1991 82077
[   28.186722] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   28.186729] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   28.186732] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   28.186749] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 2
[   28.186768] ehci_hcd 0000:00:1a.7: debug port 1
[   28.186772] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   28.186777] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[   28.190646] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.190687] usb usb2: configuration #1 chosen from 1 choice
[   28.190701] hub 2-0:1.0: USB hub found
[   28.190704] hub 2-0:1.0: 4 ports detected
[   28.294477] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   28.294482] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   28.294484] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   28.294495] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[   28.294512] ehci_hcd 0000:00:1d.7: debug port 1
[   28.294517] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   28.294521] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe7ff800
[   28.298404] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.298445] usb usb3: configuration #1 chosen from 1 choice
[   28.298460] hub 3-0:1.0: USB hub found
[   28.298462] hub 3-0:1.0: 8 ports detected
[   28.402268] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.453878] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   28.458882] ata_piix 0000:00:1f.2: version 2.11
[   28.458887] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   28.458908] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   28.458929] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.458978] scsi0 : ata_piix
[   28.459013] scsi1 : ata_piix
[   28.459069] ata1: SATA max UDMA/133 cmd 0x0001b000 ctl 0x0001ac02 bmdma 0x0001a480 irq 20
[   28.459071] ata2: SATA max UDMA/133 cmd 0x0001a880 ctl 0x0001a802 bmdma 0x0001a488 irq 20
[   28.649706] usb 3-3: new high speed USB device using ehci_hcd and address 2
[   28.787980] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   28.787991] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 20
[   28.788007] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   28.788029] scsi2 : ata_piix
[   28.788055] scsi3 : ata_piix
[   28.788110] ata3: SATA max UDMA/133 cmd 0x0001a000 ctl 0x00019c02 bmdma 0x00019480 irq 20
[   28.788112] ata4: SATA max UDMA/133 cmd 0x00019880 ctl 0x00019802 bmdma 0x00019488 irq 20
[   28.788731] usb 3-3: configuration #1 chosen from 1 choice
[   29.128983] ata4.00: ATA-8: SAMSUNG HD501LJ, CR100-11, max UDMA7
[   29.128985] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   29.136963] ata4.00: configured for UDMA/133
[   29.137024] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   29.137072] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   29.137080] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   29.137082] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   29.137098] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   29.137118] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[   29.137171] usb usb4: configuration #1 chosen from 1 choice
[   29.137185] hub 4-0:1.0: USB hub found
[   29.137188] hub 4-0:1.0: 2 ports detected
[   29.240552] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   29.240556] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.240558] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.240569] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   29.240586] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000b800
[   29.240637] usb usb5: configuration #1 chosen from 1 choice
[   29.240650] hub 5-0:1.0: USB hub found
[   29.240653] hub 5-0:1.0: 2 ports detected
[   29.344336] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   29.344340] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.344342] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.344355] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   29.344372] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000b480
[   29.344420] usb usb6: configuration #1 chosen from 1 choice
[   29.344434] hub 6-0:1.0: USB hub found
[   29.344437] hub 6-0:1.0: 2 ports detected
[   29.448124] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   29.448128] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.448130] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.448140] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   29.448157] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[   29.448207] usb usb7: configuration #1 chosen from 1 choice
[   29.448223] hub 7-0:1.0: USB hub found
[   29.448226] hub 7-0:1.0: 2 ports detected
[   29.551905] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   29.551909] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   29.551911] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   29.551922] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[   29.551939] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b080
[   29.551991] usb usb8: configuration #1 chosen from 1 choice
[   29.552004] hub 8-0:1.0: USB hub found
[   29.552006] hub 8-0:1.0: 2 ports detected
[   29.655725] r8169 Gigabit Ethernet driver 2.2LK loaded
[   29.655742] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   29.655753] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   29.655925] eth0: RTL8168b/8111b at 0xf881c000, 00:19:db:f6:0c:c0, XID 38000000 IRQ 17
[   29.657106] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.657131] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   29.657340] scsi4 : pata_marvell
[   29.657371] scsi5 : pata_marvell
[   29.657385] ata5: PATA max UDMA/100 cmd 0x0001dc00 ctl 0x0001d882 bmdma 0x0001d400 irq 16
[   29.657387] ata6: PATA max UDMA/133 cmd 0x0001d800 ctl 0x0001d482 bmdma 0x0001d408 irq 16
[   29.657401] BAR5:00:02 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:07 0D:00 0E:00 0F:00 
[   29.662133] sd 3:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   29.662140] sd 3:0:0:0: [sda] Write Protect is off
[   29.662141] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.662149] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.662176] sd 3:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   29.662181] sd 3:0:0:0: [sda] Write Protect is off
[   29.662182] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.662189] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.662191]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   29.711101] sd 3:0:0:0: [sda] Attached SCSI disk
[   29.713333] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   29.727583] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004c010700793a]
[   29.871253] Attempting manual resume
[   29.871255] swsusp: Resume From Partition 8:3
[   29.871256] PM: Checking swsusp image.
[   29.871391] PM: Resume from disk failed.
[   29.895239] kjournald starting.  Commit interval 5 seconds
[   29.895245] EXT3-fs: mounted filesystem with ordered data mode.
[   29.975413] ata5.00: ATAPI: HL-DT-STDVD-RAM GSA-H50N, 1.00, max UDMA/66
[   30.147062] ata5.00: configured for UDMA/66
[   30.147082] BAR5:00:02 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:07 0D:00 0E:00 0F:00 
[   30.314661] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H50N 1.00 PQ: 0 ANSI: 5
[   30.314703] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   34.504560] r8169: eth0: link up
[   34.504567] r8169: eth0: link up
[   34.940664] input: PC Speaker as /class/input/input2
[   35.067925] NET: Registered protocol family 10
[   35.067982] lo: Disabled Privacy Extensions
[   35.365418] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.384242] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.428513] Linux agpgart interface v0.102 (c) Dave Jones
[   35.464915] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x4117
[   35.464925] usbcore: registered new interface driver usblp
[   35.464927] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   35.598166] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   35.598169] Uniform CD-ROM driver Revision: 3.20
[   35.598208] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   35.676574] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   35.676587] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.882960] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   36.137136] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   36.384820] lp: driver loaded but no devices found
[   36.421335] coretemp coretemp.0: Using undocumented features, absolute temperature might be wrong!
[   36.421363] coretemp coretemp.1: Using undocumented features, absolute temperature might be wrong!
[   36.421382] coretemp coretemp.2: Using undocumented features, absolute temperature might be wrong!
[   36.421397] coretemp coretemp.3: Using undocumented features, absolute temperature might be wrong!
[   36.487783] Adding 2441872k swap on /dev/sda3.  Priority:-1 extents:1 across:2441872k
[   36.795391] EXT3 FS on sda2, internal journal
[   37.630957] kjournald starting.  Commit interval 5 seconds
[   37.631141] EXT3 FS on sda1, internal journal
[   37.631145] EXT3-fs: mounted filesystem with ordered data mode.
[   37.649655] kjournald starting.  Commit interval 5 seconds
[   37.649973] EXT3 FS on sda5, internal journal
[   37.649976] EXT3-fs: mounted filesystem with ordered data mode.
[   38.237595] input: Power Button (FF) as /class/input/input4
[   38.237608] ACPI: Power Button (FF) [PWRF]
[   38.237663] input: Power Button (CM) as /class/input/input5
[   38.237671] ACPI: Power Button (CM) [PWRB]
[   38.256718] No dock devices found.
[   39.248588] ppdev: user-space parallel port driver
[   39.422202] audit(1205392926.103:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5315 profile="/usr/sbin/cupsd"
[   41.756825] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.756828] apm: disabled - APM is not SMP safe.
[   42.976432] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   42.976436] vboxdrv: Successfully done.
[   42.976467] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   42.976469] vboxdrv: Successfully loaded version 1.5.6 (interface 0x00050002).
[   43.240764] Failure registering capabilities with primary security module.
[   43.382837] Bluetooth: Core ver 2.11
[   43.382880] NET: Registered protocol family 31
[   43.382883] Bluetooth: HCI device and connection manager initialized
[   43.382887] Bluetooth: HCI socket layer initialized
[   43.393094] Bluetooth: L2CAP ver 2.8
[   43.393098] Bluetooth: L2CAP socket layer initialized
[   43.429416] Bluetooth: RFCOMM socket layer initialized
[   43.429572] Bluetooth: RFCOMM TTY layer initialized
[   43.429574] Bluetooth: RFCOMM ver 1.8
[   45.136099] eth0: no IPv6 routers present
[   45.379622] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   45.396753] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   45.396782] [fglrx] ASYNCIO init succeed!
[   45.398733] [fglrx] PAT is enabled successfully!
[   45.398946] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   45.401501] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.340688] [fglrx] Reserve Block - 0 offset =  0X1fffc000 length = 0X4000
[   46.340693] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   46.340695] [fglrx] Reserve Block - 2 offset =  0Xff7f000 length = 0X80000
[   46.688405] [fglrx] interrupt source 20008000 successfully enabled
[   46.688409] [fglrx] enable ID = 0x00000006
[   46.688715] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   46.688990] [fglrx] interrupt source 10000000 successfully enabled
[   46.688993] [fglrx] enable ID = 0x00000008
[   46.689254] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   46.710318] [fglrx] interrupt source 60000001 successfully enabled
[   46.710323] [fglrx] enable ID = 0x00000009
[   46.710329] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[   46.710376] [fglrx] interrupt source 00000040 successfully enabled
[   46.710379] [fglrx] enable ID = 0x0000000A
[   46.710384] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[   46.710805] [fglrx] interrupt source ff00002c successfully enabled
[   46.710808] [fglrx] enable ID = 0x0000000B
[   46.710812] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[   46.710847] [fglrx] interrupt source ff00002d successfully enabled
[   46.710850] [fglrx] enable ID = 0x0000000C
[   46.710854] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[   46.710887] [fglrx] interrupt source 20000400 successfully enabled
[   46.710890] [fglrx] enable ID = 0x0000000D
[   46.710895] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[ 1446.671449] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 1446.959950] usb 1-1: configuration #1 chosen from 1 choice
[ 1476.948595] Linux video capture interface: v2.00
[ 1476.960625] usbcore: registered new interface driver gspca
[ 1476.960714] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
root@home-desktop:/home/home# 
  
```

---

### Post by SLA_leandrin on 2008-03-20
...--- Bump !! ---...

---

### Post by rockinlinux on 2008-03-26
still been searching high and low for this...anyone?

---

### Post by j000 on 2008-04-01
Install gspca version 1.00.20 from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) :)
Eye 110 work with it.

---


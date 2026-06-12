---
title: "Sound Card help"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by treehopper29 on 2006-06-27
I have a pretty old sound card that ubuntu wont recongnize.

Analog Devices
AD1845JP
soundport
9524
B35572.1-0.6

thats all the info I got of the card. I could use some help.

---

### Post by FuturePast on 2006-06-27
Can you open a terminal and type the commands [FONT="Courier New"]lsmod[/FONT] ,
[FONT="Courier New"]lspci[/FONT]  and [FONT="Courier New"]cat /proc/asound/cards[/FONT].

Copy and paste the results here.

---

### Post by treehopper29 on 2006-06-27
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-s [[<bus>]:][<slot>][.[<func>]]        Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-X              Show in format suitable for use in XFree86Config
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /var/lib/misc/pci.ids
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging

---

### Post by FuturePast on 2006-06-27
Just to be clear, those are three separate commands:
[FONT="Courier New"]lsmod[/FONT]<enter><copy and paste>
[FONT="Courier New"]lspci[/FONT]<enter><copy and paste>
[FONT="Courier New"]cat /proc/asound/cards[/FONT]<enter><copy and paste>

---

### Post by treehopper29 on 2006-06-27
lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
r128                   40832  1
drm                    58004  2 r128
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
acx_pci               122752  0
firmware_class          9472  1 acx_pci
pci_hotplug            24628  0
ali_agp                 6656  1
agpgart                32328  2 drm,ali_agp
dm_mod                 50364  1
evdev                   9088  0
tsdev                   7616  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
via_rhine              20356  0
mii                     5248  1 via_rhine
ohci_hcd               18564  0
usbcore               104188  2 ohci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
alim15x3               11020  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,alim15x3
unix                   24624  634
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vgModule                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
r128                   40832  1
drm                    58004  2 r128
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
acx_pci               122752  0
firmware_class          9472  1 acx_pci
pci_hotplug            24628  0
ali_agp                 6656  1
agpgart                32328  2 drm,ali_agp
dm_mod                 50364  1
evdev                   9088  0
tsdev                   7616  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
via_rhine              20356  0
mii                     5248  1 via_rhine
ohci_hcd               18564  0
usbcore               104188  2 ohci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
alim15x3               11020  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,alim15x3
unix                   24624  634
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
a16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

---

### Post by treehopper29 on 2006-06-27
lspci
0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (rev c3)
0000:00:08.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
0000:00:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c2)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

---

### Post by treehopper29 on 2006-06-27
cat /proc/asound/cards
No such file or directory

---

### Post by FuturePast on 2006-06-27
The Ubuntu sound system is the ALSA system.
From the ALSA website is seems that support for the AD1845 chip is undetermined i.e. they don't know if it works or not.
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Analog_Devices#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Analog_Devices#matrix")

I'm sorry but maybe this sound card is just too obscure...

---


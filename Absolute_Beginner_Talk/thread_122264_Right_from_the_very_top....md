---
title: "Right from the very top..."
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Simon Curran on 2006-01-27
Hi all,
 please bear with me since I am a complete Linux virgin, and generally a computer moron, so I will undoubtably be asking lots of stupid questions for an indefinate period of time.
I managed to install Breezy Badger reasonably painlessly onto my computer, but it seems that it does not want to run my soundcard (a Creative Sound Blaster Audigy LS)
I attempted to download and install a driver I was directed to via Creative support, and folowed the instructions verbatim.
The install started but for some reason failed, stating that there were some vital components missing (I don't remember precisely what they were, but I am hoping some of the more intelligent and more experienced people around here may be able to figure out what I am talking about...)
My stupid question of the day is, is it a hardware fault, or am I genuinly missing something I need to complete the install.
Many thanks in advance for any advice which can be offered.
Simon

---

### Post by adwait on 2006-01-27
You are missing some software most definitely. (IE:the correct drivers for your sound card)

---

### Post by az on 2006-01-27
What does the device manager say about your card?  Is your sound just muted?  When you double-click on the speaker icon, are all the sliders up and unmuted?  (Do you have a sound icon on the top-right?)

Also, from a terminal type and post the output from

lspci
lsmod

---

### Post by Simon Curran on 2006-01-28
Hi again guys, thanks for trying to help.
lspci says;
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0b.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:0f.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:00:0f.1 Input device controller: Creative Labs SB Audigy LS MIDI/Game port
0000:00:13.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:13.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:13.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]


and lsmod says;

Module                  Size  Used by
binfmt_misc            10888  1
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
radeon                 68352  1
drm                    58004  2 radeon
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  4
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
emu10k1_gp              3712  0
gameport               14472  2 emu10k1_gp
rt2500                150372  1
i2c_sis96x              5252  0
i2c_sis630              7308  0
i2c_core               19728  3 i2c_acpi_ec,i2c_sis96x,i2c_sis630
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
sis_agp                 8452  1
agpgart                32328  2 drm,sis_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
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
ehci_hcd               29448  0
uhci_hcd               28048  0
sis900                 19456  0
mii                     5248  1 sis900
ohci_hcd               18564  0
usbcore               104316  4 ehci_hcd,uhci_hcd,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
sis5513                14472  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,sis5513
unix                   24624  613
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


I'm hoping that all makes sense to some of you guys, because for me it might as well be Greek...

Thanks again
Simon

---

### Post by Simon Curran on 2006-01-28
[QUOTE=azz]What does the device manager say about your card?  Is your sound just muted?  When you double-click on the speaker icon, are all the sliders up and unmuted?  (Do you have a sound icon on the top-right?)

Also, from a terminal type and post the output from

lspci
lsmod[/QUOTE]


Nearly forgot, I have no speaker speaker icon, the device manager seems to be able to see my card, and I'm not quite sure where to look for the muting.

Again thanks
Simon

---


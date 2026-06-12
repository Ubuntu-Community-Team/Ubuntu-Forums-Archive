---
title: "How do you get sound working?"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by holycow on 2005-07-10
Ok,
I have read all the posting I can find and still have no luck getting my sound card working.
I am attaching two files screenshots of device manager in Gnome along with the the output from lsmod and lspci.

root@dell:/etc # lsmod
Module                  Size  Used by
snd_pcm_oss            48168  0
snd_pcm                85540  1 snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_timer              23172  1 snd_pcm
snd_mixer_oss          16640  1 snd_pcm_oss
snd                    50660  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
sb_lib                 44720  0
uart401                11460  1 sb_lib
sound                  75308  2 sb_lib,uart401
soundcore               9824  3 snd,sb_lib,sound
asus_acpi              11800  0
nls_iso8859_1           4352  0
nls_cp437               6016  0
vfat                   13312  0
fat                    41792  1 vfat
isofs                  33976  0
udf                    79876  0
usb_storage            59200  0
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  10
af_packet              20872  0
ath_pci                50724  0
wlan                  105564  2 ath_pci
ath_hal               129232  2 ath_pci
tg3                    74500  0
piix                   12576  1
ehci_hcd               27780  0
uhci_hcd               29328  0
usbcore               104292  5 usb_storage,ehci_hcd,uhci_hcd
pci_hotplug            30640  0
parport_pc             32064  1
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_generic             1664  0
ide_disk               16768  0
ide_cd                 38276  0
ide_core              125272  5 usb_storage,piix,ide_generic,ide_disk,ide_cd
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
sd_mod                 20480  3
ata_piix                7940  4
libata                 36356  1 ata_piix
scsi_mod              115148  3 usb_storage,sd_mod,libata
unix                   26160  772
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

root@dell:/etc # lspci
0000:00:00.0 Host bridge: Intel Corp. Server Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. Server Memory Controller Hub PCI Express Port (rev 04)
0000:00:02.0 Display controller: Intel Corp. Graphics Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:04:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)
0000:04:01.0 Multimedia audio controller: VLSI Technology Inc Thunderbird (rev 06)
0000:04:01.1 Input device controller: VLSI Technology Inc Thunderbird
0000:04:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

It appears that the sound card is an VLSI Thunderbird.
Any ideas on how to get it working, please let me know!

---

### Post by manicka on 2005-07-10
open the volume control panel (right click on volume icon and choose open volume control) and make sure that none of the volumes are muted.

Is this card an onboard one?

---

### Post by Error_Msg on 2005-07-10
Go to the sound settings and set it to ALSA. Then open a terminal and type killall esd.
HTH

E_M

---

### Post by holycow on 2005-07-11
[QUOTE=Error_Msg]Go to the sound settings and set it to ALSA. Then open a terminal and type killall esd.
HTH

E_M[/QUOTE]
After changing to ALSA, , a new pop up windows comes up which displays the followong:

Sound server informational message:
Error while initializing the sound driver:
device /dev/audio can't be opened (No such device)
The sound server will continue, using the null output device.

also, there was nothing muted.

I give.

 :|

---

### Post by Mr. Electric Wizard on 2005-07-11
ALSA didn't work for me, but eSound did...

---

### Post by Error_Msg on 2005-07-11
[QUOTE=holycow]After changing to ALSA, , a new pop up windows comes up which displays the followong:

Sound server informational message:
Error while initializing the sound driver:
device /dev/audio can't be opened (No such device)
The sound server will continue, using the null output device.

also, there was nothing muted.

I give.

 :|[/QUOTE]

No way man, don't give up now! The best is yet to come!
Your problem exceeds my expertise. 
Try in the hardware help forum.
BTW, how many FPS do you get with that Voodoo3 when you run glxgears?

E_M

---

### Post by rider343 on 2005-07-11
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

### Post by holycow on 2005-07-11
OK, call me a wimp.
I just snagged a old SoundBlaster PCI and it worked without having to change a thing!
I guess this Philips card will go to the spare parts pile.

Thanks all that helped!

---


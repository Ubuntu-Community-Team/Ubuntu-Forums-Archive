---
title: "problems with sound in dapper drake"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by qrm on 2006-05-21
Hi !

This is my third ubuntu install on this computer and sound has worked flawlessly until now. When i try to open volume control i get the following error:

No volume control GStreamer plugins and/or devices found

Ive been googeling around and this is what Ive tried:

cat /proc/asound/modules - doesnt tell me anything, the folder "modules" doesnt even exist in /proc/asound

sudo gst-register-0.8 - It tells me that Loaded 151 plugins with 305 features. but I cant find anything like gstreamer or alike from the list

My sound card is a onboard one and the device manager shows tht it should be 82801EB/ER (ICH5/ICH5R) AC'97 Audio

Thanks in advance!

EDIT. when i try to get to alsamixer from the terminal it tells me:
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by qrm on 2006-05-22
well, i went the easier way and just reinstalled my ubuntu. I havent upgraded it to dapper drake yet but atleast now my sound is working again. Still i get the sound error messages with xmms saying i should check if no other aplication is blocking my sound etc

---

### Post by qrm on 2006-05-22
doublepost :x

---

### Post by Sef on 2006-05-22
> 82801EB/ER (ICH5/ICH5R) AC'97 Audio

Audio '97 has been problematic in Dapper for some reason.  

First three basic questions:

1) Have you installed the codecs?

[http://wiki.ubuntu.com/RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")

2) Right click on the sound icon.  Is the sound unmuted?

3) Is 82801EB/ER (ICH5/ICH5R) AC'97 Audio set as your default?  (System > Preferences > Sound)

Two terminal commands to copy and paste in this thread:

1) cat /proc/asound/cards

2) gksudo gedit /etc/modrprobe.d/alsa-base

---

### Post by llamakc on 2006-05-23
Similar problem here:

```

$ cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC655 at 0xfebfd000, irq 225

```

```

cat /etc/modprobe.d/alsa-base # autoloader aliases install sound-slot-0 modprobe snd-card-0 install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

```

```

 lspci
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f2)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f2)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:05:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
0000:05:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

```

and 

```

 lsmod
Module                  Size  Used by
binfmt_misc            13192  1
rfcomm                 44244  0
l2cap                  29184  5 rfcomm
bluetooth              54244  4 rfcomm,l2cap
ipv6                  287456  22
fglrx                 479836  7
agpgart                37072  1 fglrx
ppdev                  10116  0
cpufreq_userspace       6816  0
cpufreq_stats           6912  0
freq_table              5152  1 cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
video                  16644  0
tc1100_wmi              7172  0
sony_acpi               5900  0
pcc_acpi               12736  0
hotkey                 11812  0
dev_acpi               11652  0
container               4928  0
button                  6992  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
ac                      5508  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
af_packet              25224  4
nls_cp437               6208  1
ntfs                  114288  1
dm_mod                 63640  1
md_mod                 76244  0
psmouse                40196  0
lp                     12612  0
rtc                    14388  0
floppy                 65924  0
parport_pc             38340  1
parport                39560  3 ppdev,lp,parport_pc
bcm43xx               138892  0
ieee80211softmac       32384  1 bcm43xx
ieee80211              40072  2 bcm43xx,ieee80211softmac
pcspkr                  2564  0
ieee80211_crypt         6848  1 ieee80211
shpchp                 49376  0
pci_hotplug            30916  1 shpchp
snd_intel8x0           35740  2
snd_ac97_codec         98912  1 snd_intel8x0
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  2 snd_pcm_oss
snd_pcm                96772  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  1 snd_pcm
snd                    60068  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11040  2 snd
snd_page_alloc         11592  2 snd_intel8x0,snd_pcm
i2c_nforce2             7360  0
i2c_core               23168  2 i2c_acpi_ec,i2c_nforce2
tsdev                   8320  0
evdev                  10432  1
ext3                  148296  3
jbd                    65684  1 ext3
usbhid                 41312  0
ide_generic             1792  0
forcedeth              25860  0
ehci_hcd               33800  0
ohci_hcd               22788  0
usbcore               137476  4 usbhid,ehci_hcd,ohci_hcd
ide_disk               19584  8
generic                 5444  0
amd74xx                15132  0 [permanent]
sata_nv                10180  0
libata                 84176  1 sata_nv
scsi_mod              145736  1 libata
thermal                14088  0
processor              26696  1 thermal
fan                     5124  0
capability              5256  0
commoncap               7616  1 capability
vga16fb                14344  1
vgastate               10304  1 vga16fb
fbcon                  44640  72
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              2752  1 bitblit

```

I threw my hd's into an extra box and can't get sound working on this mobo. Any ideas?

---

### Post by Sef on 2006-05-23
Here's how I got mine working.

> # Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

First comment the next to last line by using a # before it.

Second in the last line change the -2 to a 0.

It shoud look like this now.

> # Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=0

---

### Post by qrm on 2006-05-26
i got rid of this problem with reinstalling ubuntu and upgrading it again to dapper drake. Hopefully this bug will be fixed, if not in this relase of ubuntu then in edgy edge

---

### Post by llamakc on 2006-05-26
Rolling back to kernel 2.6.15-22-k7 did the trick for me. I'll never reinstall a deb-based distribution to fix a problem though. Easy enough to just roll back a kernel or reinstall a persnickety package with dpkg-reconfigure -plow nameofpackage. . . .

---

### Post by BoyOfDestiny on 2006-05-26
[QUOTE=qrm]well, i went the easier way and just reinstalled my ubuntu. I havent upgraded it to dapper drake yet but atleast now my sound is working again. Still i get the sound error messages with xmms saying i should check if no other aplication is blocking my sound etc[/QUOTE]

An application is blocking them, ESD.

open up a terminal and type

sudo killall ESD

If that works for you, you can disable in System -> Preferences -> Sound, and uncheck enable sound server...

Other than that, you can try and make xmms output with ALSA...

---

### Post by j823777 on 2006-05-27
I fixed this by opening volume control, making the four VIA DXS tracks visible and then cranking up the volume...

---

### Post by screamz on 2006-06-01
after upgrading from breezy to dapper
my soundcard isn t detected

[http://pastebin.com/752228](http://pastebin.com/752228)

here s some output

does anyone have a suggestion?

---


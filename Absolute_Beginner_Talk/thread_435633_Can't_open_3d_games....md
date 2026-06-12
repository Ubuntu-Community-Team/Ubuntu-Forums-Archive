---
title: "Can't open 3d games..."
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by dasan on 2007-05-07
When i am opening a game eroor msg comes "3d acceleration is off" how to make it On ?
Also my system hangs.........
What i should Do ?
Please help..............

---

### Post by Swankyman on 2007-05-07
hey,

why dont you search the forums for your graphic card and see if anyone else has problems with it. Also we need more info to help you. 

what version of ubuntu?
what graphics card you have. 
paste the output of the lspci command executed in the terminal
and also the output of lsmod

rich

---

### Post by dasan on 2007-05-07
ispci-----
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

---

### Post by dasan on 2007-05-07
lsmod-----------
Module                  Size  Used by
binfmt_misc            11272  1 
rfcomm                 37660  0 
l2cap                  22276  5 rfcomm
bluetooth              51300  4 rfcomm,l2cap
via                    43136  2 
drm                    79380  3 via
cpufreq_userspace       4116  0 
cpufreq_stats           5508  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        7676  0 
freq_table              4740  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     6560  0 
af_packet              20872  0 
nls_iso8859_1           4224  1 
nls_cp437               5888  1 
vfat                   12800  1 
fat                    52380  1 vfat
fuse                   44436  5 
lp                     11332  0 
snd_via82xx            27672  1 
gameport               15112  1 snd_via82xx
snd_pcm_oss            43264  0 
snd_mixer_oss          16512  1 snd_pcm_oss
snd_via82xx_modem      14856  0 
snd_ac97_codec         97184  2 snd_via82xx,snd_via82xx_modem
parport_pc             34980  1 
ac97_bus                2304  1 snd_ac97_codec
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_seq_midi            8576  0 
snd_pcm                76680  4 snd_via82xx,snd_pcm_oss,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart         8320  1 snd_via82xx
parport                35272  2 lp,parport_pc
rtc                    13104  0 
snd_rawmidi            24448  2 snd_seq_midi,snd_mpu401_uart
snd_seq_midi_event      7424  2 snd_seq_oss,snd_seq_midi
snd_seq                49648  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                37640  0 
k8temp                  5760  0 
pcspkr                  3072  0 
serio_raw               6916  0 
shpchp                 33300  0 
pci_hotplug            31160  1 shpchp
i2c_viapro              9108  0 
amd64_agp              12804  1 
snd                    51716  14 snd_via82xx,snd_pcm_oss,snd_mixer_oss,snd_via82xx_modem,snd_ac97_codec,snd_seq_oss,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc          9992  3 snd_via82xx,snd_via82xx_modem,snd_pcm
i2c_core               21776  1 i2c_viapro
agpgart                34096  2 drm,amd64_agp
tsdev                   7872  0 
evdev                  10112  1 
ipv6                  252512  8 
ext3                  129288  1 
jbd                    53032  1 ext3
mbcache                 8196  1 ext3
sg                     35484  0 
sd_mod                 22292  3 
floppy                 58020  0 
via_rhine              23816  0 
mii                     5632  1 via_rhine
ehci_hcd               32780  0 
uhci_hcd               23952  0 
usbcore               131480  3 ehci_hcd,uhci_hcd
via82cxxx               9476  0 [permanent]
sata_via               11652  7 
ata_generic             8196  0 
libata                125208  2 sata_via,ata_generic
scsi_mod              141580  3 sg,sd_mod,libata
generic                 4228  0 [permanent]
raid10                 24704  0 
raid456               123408  0 
xor                    15752  1 raid456
raid1                  23936  0 
raid0                   8704  0 
multipath               8832  0 
linear                  6400  0 
md_mod                 77076  7 raid10,raid456,raid1,raid0,multipath,linear
thermal                13832  0 
processor              22956  1 thermal
fan                     4740  0 
dm_mod                 57164  10 
fbcon                  41760  0 
tileblit                2688  1 fbcon
font                    8320  1 fbcon
bitblit                 6016  1 fbcon
softcursor              2304  1 bitblit
vesafb                  8196  0 
capability              5000  0 
commoncap               7296  1 capability

---

### Post by Swankyman on 2007-05-07
Hi again,

Sorry forgot can you post your /etc/X11/xorg.conf file

Looking at your lspci and lsmod it looks like the driver for your S3 Unichrome Pro card are loaded. They are the ones in lsmod called via and drm 

But I think there is maybe problem with the X-org config as shown in this thread:

[http://ubuntuforums.org/showthread.php?t=420688&highlight=S3+Unichrome+Pro+VGA+Adapter](http://ubuntuforums.org/showthread.php?t=420688&highlight=S3+Unichrome+Pro+VGA+Adapter)

post your xorg.conf and we´ll  have a look!!

rich

---

### Post by dasan on 2007-05-09
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480"
                EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
                                                              145,1         Bot

---

### Post by Swankyman on 2007-05-09
Hey,

why not try this

replacing this section 

Section "Device"
Identifier "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
Driver "via"
BusID "PCI:1:0:0"
EndSection


with

Section "Device"
Identifier "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
Driver "via"
BusID "PCI:1:0:0"
Option "DisableIRQ"
Option "VBERestore" "true"
EndSection

using 

sudo gedit /etc/X11/xorg.conf

this guy seems to think it helps

[http://ubuntuforums.org/showthread.php?t=420688&highlight=S3+Unichrome+Pro+VGA+Adapter](http://ubuntuforums.org/showthread.php?t=420688&highlight=S3+Unichrome+Pro+VGA+Adapter)

Rich

---

### Post by slimdog360 on 2007-05-09
nevermind

---

### Post by Enverex on 2007-05-09
I'd get the output of "glxinfo" too, that'll tell you what's going on with accelleration and the drivers themselves.

But in all honesty I don't know what you expect to run, that is, apparently THE worst performing onboard laptop "graphics card" in existance, so I don't think you're going to be able to run anything anyway.

---

### Post by dasan on 2007-05-11
Now again it is not opening.............................:mad:

---


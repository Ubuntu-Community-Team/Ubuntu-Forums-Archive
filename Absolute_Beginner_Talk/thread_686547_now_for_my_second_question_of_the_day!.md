---
title: "now for my second question of the day!"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by recycledhippy on 2008-02-03
I have a ATI Radeon 9250 graphics card in my computer. I don't think it's working to it's fullest potential. How can I check to see if it is or if I need to get a driver or whatever.

---

### Post by jan quark on 2008-02-03
first check in

system > administration > restricted drivers manager

is there some ati drivers inactive ?

---

### Post by recycledhippy on 2008-02-03
just one for the onboard nvidia graphics which I'm not using

---

### Post by schaumkeks on 2008-02-03
> **recycledhippy said:**
> I have a ATI Radeon 9250 graphics card in my computer. I don't think it's working to it's fullest potential. How can I check to see if it is or if I need to get a driver or whatever.

Check, if directing rendering is enabled.
```
glxinfo | grep direct
```

---

### Post by recycledhippy on 2008-02-03
glxinfo | grep direct

direct rendering: Yes

---

### Post by schaumkeks on 2008-02-03
> **recycledhippy said:**
> glxinfo | grep direct

direct rendering: Yes
So you have hardware acceleration with the default drivers (radeon). All should be fine or have you found anything specific that doesn't work?

---

### Post by recycledhippy on 2008-02-03
if I try to enable visual effects to normal everything gets real choppy in performance and if I try to enable it to extra it will tell me I need to enable 3d acceleration on my nvidia graphics, but thats my onboard that I'm not using

---

### Post by recycledhippy on 2008-02-03
any thoughts?

---

### Post by recycledhippy on 2008-02-03
bump

---

### Post by schaumkeks on 2008-02-03
> **recycledhippy said:**
> if I try to enable visual effects to normal everything gets real choppy in performance and if I try to enable it to extra it will tell me I need to enable 3d acceleration on my nvidia graphics, but thats my onboard that I'm not using

Maybe it's better to disable the on-board graphics. Is this possible within the BIOS?
If not, one could try to blacklist the appropriate kernel module. But I don't know which is the right one for your chip.

What does the following command show?
```
sudo lshw -C display
```

---

### Post by recycledhippy on 2008-02-03
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

 bios is set to read the pci slot not onboard

---

### Post by schaumkeks on 2008-02-03
This out put doesn't help :) Have you entered the command exactly as I wrote? It is an uppercase C.

---

### Post by recycledhippy on 2008-02-03
*-display:0             
       description: VGA compatible controller
       product: RV280 [Radeon 9200 PRO]
       vendor: ATI Technologies Inc
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga bus_master cap_list
       configuration: latency=32 mingnt=8
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 PRO] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 6.1
       bus info: pci@0000:01:06.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8
  *-display
       description: VGA compatible controller
       product: NV18 [GeForce4 MX - nForce GPU]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga cap_list
       configuration: latency=32 maxlatency=1 mingnt=5

---

### Post by schaumkeks on 2008-02-03
I guess the kernel module for the nvidia graphics chip is called "nvidia". Could you check if it is listed with
```
lsmod
```

You can then add the line
```
blacklist nvidia
``` to the end of the file /etc/modprobe.d/blacklist and run
```
sudo depmod -a
``` and reboot.

Then check if the nvidia entry is gone from the output of
```
sudo lshw -C display
```

You should also check if your /etc/X11/xorg.conf is setup right.

---

### Post by recycledhippy on 2008-02-04
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
button                  8976  0 
sbs                    19592  0 
ac                      6148  0 
dock                   10656  0 
container               5504  0 
video                  18060  0 
battery                11012  0 
lp                     12580  0 
sg                     36764  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
sd_mod                 30336  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
usblp                  15104  0 
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
psmouse                39952  0 
i2c_nforce2             7040  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  1 i2c_nforce2
nvidia_agp              9756  1 
agpgart                35016  2 drm,nvidia_agp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  6 
ata_generic             8452  0 
libata                125168  1 ata_generic
usb_storage            73024  0 
scsi_mod              147084  4 sg,sd_mod,libata,usb_storage
libusual               18448  1 usb_storage
amd74xx                15260  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,amd74xx
forcedeth              51592  0 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  6 usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

AS you can see I have a nvidiaagp do you think I should do that one? 
If I type /etc/x11/xorg.conf it says no such file or directory

---

### Post by schaumkeks on 2008-02-04
Better not. I'm no expert, but I think this is needed by your ATI card. But I got another idea. Please check the AGP status with
```
cat /proc/driver/nvidia/agp/status
```

> If I type /etc/x11/xorg.conf it says no such file or directory
Again it is an uppercase X11 :)

By the way, is it possible to change the thread subject? This one says nothing...

---

### Post by recycledhippy on 2008-02-04
I have to watch the upper case!

bash: /etc/X11/xorg.conf: Permission denied

and my ATI graphic card is pci not agp. In the bios you can pick it to read pci slot or agp, onboard for some reason you dont have seperate choices for agp  and onboard they're the same thing

---

### Post by schaumkeks on 2008-02-04
> **recycledhippy said:**
> I have to watch the upper case!

bash: /etc/X11/xorg.conf: Permission denied

and my ATI graphic card is pci not agp. In the bios you can pick it to read pci slot or agp, onboard for some reason you dont have seperate choices for agp  and onboard they're the same thing

Well then you could try to "blacklist nvidia-agp". Don't forget changes in /etc have to be done as superuser:
```
gksudo gedit /etc/modprobe.d/blacklist
```

Same goes for
```
gksudo gedit /etc/X11/xorg.conf
```
This is a file no executable.

---

### Post by recycledhippy on 2008-02-04
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:6:0"
EndSection

Section "Monitor"
	Identifier	"HW191A"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"HW191A"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by recycledhippy on 2008-02-04
Im going to start a new thread called blacklisting onboard graphics. look for it

---


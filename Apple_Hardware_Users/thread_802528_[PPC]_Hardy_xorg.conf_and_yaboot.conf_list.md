---
title: "[PPC] Hardy xorg.conf and yaboot.conf list"
date: 2008-05-21
forum: Apple Hardware Users
---

### Post by stream303 on 2008-05-21
For some, getting Hardy to work on your PPC box may sometimes require manually editing your **/etc/X11/xorg.conf** file, and also your **/etc/yaboot.conf**.

Although the stickies and faqs are great, it might be easier to consolidate **known working configurations** for Hardy with examples.  They may not be optimal, but will at least bring you to a point of usability.

While copying over pre-Hardy xorg.conf files might work, I'd like to see them pared down to just what you need with Hardy's default xorg.conf.  If you look at your /var/log/Xorg.0.log file, you might see if what you needed was already picked up by Hardy's configuration, or rejected.

A quick reminder:  edits to /etc/yaboot.conf don't take affect unless you make them permanent.  That is, after editing, do

```
sudo ybin -v -C /etc/yaboot.conf
```

With that in mind, I'll kick it off and see how it goes...

---

### Post by stream303 on 2008-05-21
**Model:  2005 Rev-A G5 20" iMac** (no als, no camera)

(My edits in **BOLD**)

**Snippet from lspci :**
nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)

**my /proc/cpuinfo**:
```
processor	: 0
cpu		: PPC970FX, altivec supported
clock		: 900.000000MHz
revision	: 3.0 (pvr 003c 0300)

timebase	: 33333333
platform	: PowerMac
machine		: PowerMac8,1
motherboard	: PowerMac8,1 MacRISC4 Power Macintosh 
detected as	: 338 (iMac G5)
pmac flags	: 00000000
L2 cache	: 512K unified
pmac-generation	: NewWorld
```

Also:
[http://www.everymac.com/systems/apple/imac/stats/imac_g5_1.8_20.html](http://www.everymac.com/systems/apple/imac/stats/imac_g5_1.8_20.html)

**My working /etc/X11/xorg.conf** (edited)

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "mac"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        **Option          "FPDither" "true"**
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

**My /etc/yaboot.conf** :

```
boot=/dev/sda2
device=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        **append="nosplash"**

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        **append="nosplash"**
```

**Notes:**  The FPDither option provides a better looking screen when using some lcd's with nvidia cards.  Note that this isn't ppc-specific so it works on other architectures as well.
Without the "nosplash" parameter, the system would boot with a black screen and only come to life when it reached the GDM gui login.  This way, I can see dmesg scroll past during the boot.

---

### Post by frog_pilot on 2008-05-21
I will attach my confs as soon as I'm back in ubuntu,

But I've got a question first: The posted command ```
sudo ybin -v -C /etc/yaboot.conf
``` I wondered what function the parameter "-C /etc/yaboot.conf" has got. For me everytime I had to use it a simply ```
sudo ybin
``` worked: the ddefault yaboot file /etc/yaboot.conf was loaded onto the boot volume. Usualy I add the parameter ```
-v
``` to see detailed output, because without this parameter there is no graphical output of the command at all. Can you specify a certain config file with the parameter ```
-C
```. Could you use e.g. ```
sudo ybin -v -C /media/sdb4/configbak/yaboot.conf.bak
```, if I would have a valid backup of my original yaboot.conf at this location?

I ask this because of my suggestion [here]("http://ubuntuforums.org/showpost.php?p=5010871&postcount=4")... :)

//edit: On the [ybin manpage]("http://hermes.ppckernel.org/cgi-bin/man/man2html?8+ybin") you can find option ```
-C
``` for specifying the configuration file > -C, --config: config-file
Use config-file as the ybin/yaboot ( 8 ) configuration file instead of the default   /etc/yaboot.conf.

---

### Post by nhamze on 2008-05-21
Could someone please post the xorg file for a clamshell running hardy

Nick

---

### Post by stream303 on 2008-05-22
> **frog_pilot said:**
> I wondered what function the parameter "-C /etc/yaboot.conf" has got.

It is just a personal habit.  I liked to get into the habit of using fully qualified pathnames when editing system files.  Not only does it help me remember where things are at, but I forced myself to use it when I botched some yaboots when I had multiple yaboot.conf files on the system - one on the internal drive and one on the firewire drive, which lived at

/media/disk/etc/yaboot.conf

As I got comfortable with constantly tinkering with yaboot, my fingers would fly fast without thinking and got me really confused. :)  Usually happens about 6 hours before work when I should have been sleeping. :)

---

### Post by frog_pilot on 2008-05-22
Model [PowerMac G4 MDD (2003) Dual 1,25 GHz]("http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_1.25_mdd.html") 2 GB RAM, Radeon 9000 Pro 64 MB VRAM (RV 250 chip)

```
**cat /proc/cpuinfo**
```
```
processor	: 0
cpu		: 7455, altivec supported
clock		: 1249.999995MHz
revision	: 0.3 (pvr 8001 0303)
bogomips	: 83.20

processor	: 1
cpu		: 7455, altivec supported
clock		: 1249.999995MHz
revision	: 0.3 (pvr 8001 0303)
bogomips	: 83.20

total bogomips	: 166.40
timebase	: 41659304
platform	: PowerMac
machine		: PowerMac3,6
motherboard	: PowerMac3,6 MacRISC2 MacRISC Power Macintosh
detected as	: 129 (PowerMac G4 Windtunnel)
pmac flags	: 00000010
L2 cache	: 256K unified
pmac-generation	: NewWorld
```

**hardy xorg.conf** - (almost default):
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"mac"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 24
		Virtual 1600 1200
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

**pre hardy xorg.conf** with 3d accel
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc107"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
#	Option		"UseFBDev"	"true"
	Option		"NoInt10"	"yes"
	Option		"AGPMode"	"4"
	Option 		"AGPFastWrite" 	"1"
	Option 		"EnablePageFlip" "1"
	Option 		"ColorTiling" 	"1"
#	Option		"RenderAccel"	"true"
EndSection

Section "Monitor"
    Identifier     "P110"
    DisplaySize     402    302
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 160.0
    Option         "DPMS"
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Monitor		"P110"
	DefaultDepth	24
   SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

**and my yaboot.conf** - default(whole system - volumes newworldbootblock, root, swap home on a second physical harddrive attached to the ATA100 bus - hdb)
```
boot=/dev/hdb2
device=/pci@f4000000/ata-6@d/disk@1:
partition=3
root=/dev/hdb3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda10

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
```

---

### Post by stream303 on 2008-05-23
Wow, nice report!

It is interesting that in the Hardy xorg.conf, you had to use the "virtual 1600 1200" line all by itself.  Was this just because the gdm login screen was way out, or was this needed overall as opposed to the more common

Modes "1600x1200"

Thanks for the writeup.

---

### Post by frog_pilot on 2008-05-23
I used it only because of the gdm default screen solution - it was widescreen on my 3:4 display.

setting max screen solution with gnome running wasnt a problem.

---

### Post by mchladek on 2008-05-26
12" iBook G4 800Mhz (changes in bold)

cpuinfo:

```
processor	: 0
cpu		: 7455, altivec supported
clock		: 798.720000MHz
revision	: 0.3 (pvr 8001 0303)
bogomips	: 48.41
timebase	: 18432000
platform	: PowerMac
machine		: PowerBook6,3
motherboard	: PowerBook6,3 MacRISC3 Power Macintosh
detected as	: 287 (iBook G4)
pmac flags	: 0000001b
L2 cache	: 256K unified
pmac-generation	: NewWorld
```

graphics:

```
ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)
```

yaboot.conf:

```
boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	**append="nosplash video=radeonfb:1024x768-24@60"**

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	**append="nosplash video=radeonfb:1024x768-24@60"**
```

xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"mac"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Section "Device"
	[B]Identifier	"ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)]"
        Driver		"radeon"[/B]
	BusID		"PCI:0:16:0"
	[B]Option		"UseFBDev"		"false"
        Option		"AGPMode"		"4"
        Option		"AGPFastWrite"		"true"
	Option		"AccelMethod"		"exa"
	Option		"RenderAccel"		"true"
	Option		"AddARGBLXVisuals"	"true"
	Option		"XAANoOffscreenPixmaps"	"true"
	Option		"DynamicClocks"		"true"[/B]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	**Device		"ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)]"**
EndSection

Section "ServerLayout"
**	Option		"AIGLX"	"True"**
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

[B]Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection[/B]
```

Note, however, that my xorg.conf file is not the bare minimum needed to boot successfully.  I made some adjustments to get compiz-fusion working smoothly.

---

### Post by mfox on 2008-05-27
What's in the xorg.conf file for the trackpad component of the 12" ibook?  I want to fix mine (15" PB G4/1.33 Al) to make the tap work permanently.

---

### Post by mchladek on 2008-05-27
> **mfox said:**
> What's in the xorg.conf file for the trackpad component of the 12" ibook?  I want to fix mine (15" PB G4/1.33 Al) to make the tap work permanently.

I'm not for sure about your PowerBook, but my iBook doesn't have a synaptics trackpad so I'm not able to use that driver in my xorg.conf.  Instead I have to execute the following on startup:

```
sudo trackpad tap
sudo trackpad lock
sudo trackpad drag
```

---

### Post by mfox on 2008-05-27
Thanks, mchladek; that's what I do at present with the tap only.  What I'm trying to achieve is to make the command "stick" so that I don't have to re-enter it each time I boot up.

---

### Post by oswaldkelso on 2008-05-27
Here is my up to date multi distro yaboot.conf it from debian but identical to the ubuntu one. suse is not working? lilo distros seem to get confused. I think some distros may be booting off the debian kernel as after pressing L for linux and tab to select the distro some  then need started in the open firmware prompt. 

$$25-05-2008
## yaboot.conf generated by the debian-installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=4
root=/dev/hda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
enableofboot

macosx=/pci@f2000000/ADPT,29160@13/@0:2

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

image=/boot/vmlinux
        root=/dev/hda3
        label=ubuntu
        read-only
        device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
	#device=hda:
	partition=3
	initrd=/boot/initrd.img

image=/boot/vmlinux
        root=/dev/hda5
        label=hda5
        read-only
        device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
	#device=hda:
	partition=5
	initrd=/boot/initrd.img

image=/boot/vmlinux
        root=/dev/hda6
        label=debian-root
        read-only
        device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
	#device=hda:
	partition=6
	initrd=/boot/initrd.img



##fedora8
image=/boot/vmlinuz-2.6.23.1-42.fc8
root=/dev/hda7
label=fedora
read-only
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
#device=hda:
partition=7
initrd=/boot/initrd-2.6.23.1-42.fc8.img


##yellowdog6
image=/boot/vmlinux-2.6.23-9.ydl6.1
root=/dev/hda8
label=yd
read-only
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
#device=hda:
partition=8
initrd=/boot/initrd-2.6.23-9.ydl6.1.img

## slackware
image=/boot/vmlinux
root=/dev/hda9
label=slack
read-only
#device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
	#device=hda:
	partition=9
	#initrd=/boot/initrd.img


#################################

## suse
# Modified by YaST2. Last modification on Mon May  5 22:33:43 BST 2008
#activate
#timeout = 80
#default = linux
#boot = /dev/hda2
#macos_timeout = 5
bootfolder = /boot/vmlinux-2.6.20.2-2-default
initrd = /boot/vmlinux-2.6.20.2-2-default


## suse
image=/boot/vmlinux-2.6.20.2-2-default
label=suse
root=/dev/hda10
#device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
#device=hda:
#partition=10
read-only
initrd = /boot/vmlinux-2.6.20.2-2-default


#######################

#arch
image=/boot/vmlinux
        root=/dev/hda11
        label=arch
        read-only
        #device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
	#device=hda:
	#partition=11
	initrd=/boot/initrd.img

£££££££££££££££££££££££££££££££££££££££££££

My xorg.conf is standard

---


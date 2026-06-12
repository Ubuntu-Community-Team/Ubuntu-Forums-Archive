---
title: "Help with laptop"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by spurgetech on 2006-02-11
I am a complete Linux noob, but pretty tech savy, lookin to learn Linux. I just installed Ubuntu version 5.10 on my laptop. I took all the defaults. I have 2 problems, well, 3.
Laptop is a Dell C610
Problem 1) trackpad does not work unless I have an external mouse attached at start up. I can disconnect after and it works fine, but if not attached at start it keeps pullin pointer to the upper or lower left corner and is unusable.
Problem 2) Fans do not seem to be working and Laptop is gettin REALLY hot.
Problem 3) I have seen both of the problems addressed int the laptop hardware section, But I confess that I am lost when they talk about the fixes. I know pretty much nothing about this stuff and need step by step, idiot proof instructions. I really want to learn but I need these fixed so I can start learning.
Please, if anyone who is willing to do a little hand holding for a noob who desires to be a guru someday, please resond.

---

### Post by christhemonkey on 2006-02-11
If you plug an external mouse in after boot up, and then remove it, does this problem still occur? (not a very feasible solution, but part of the cure!).

---

### Post by spurgetech on 2006-02-11
If I plug the mouse in while it boots and remove it after boot the trackpad works.

---

### Post by christhemonkey on 2006-02-12
Ok, try making a list of the modules that are loaded when you put an external mouse in.
Go to a terminal and type:
```
lsmod
```
Then do this again when you boot up without the external mouse.
See if there are any modules that are not loaded.

---

### Post by spurgetech on 2006-02-12
OK, here is the output with the mouse attached at start up:
> Module                  Size  Used by
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_ich           5132  0
speedstep_lib           4228  1 speedstep_ich
af_packet              20232  2
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
orinoco_cs              8456  1
orinoco                33932  1 orinoco_cs
hermes                  6912  2 orinoco_cs,orinoco
pcmcia                 24584  7 orinoco_cs
radeon                 68352  1
drm                    58004  2 radeon
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
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
yenta_socket           22540  4
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  2 drm,intel_agp
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
3c59x                  37544  0
mii                     5248  1 3c59x
uhci_hcd               28048  0
usbcore               104316  2 uhci_hcd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  3 ide_disk,ide_generic,piix
unix                   24624  679
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


And so you have no doubt I am a total noob, could you please tell me how I can access the terminal without using a mouse or trackpad. Is there a key command?
Thanks

---

### Post by christhemonkey on 2006-02-12
Ctrl+alt+F1
gets you to  a terminal
(from F1 to F4)

Not could you do the same but for when you boot without mouse!

---

### Post by spurgetech on 2006-02-12
OK, here is the results of lsmod when I start with no mouse attached:
> Module                  Size  Used by
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
af_packet              20232  2 
speedstep_ich           5132  0 
speedstep_lib           4228  1 speedstep_ich
cpufreq_userspace       4444  1 
cpufreq_stats           5124  0 
freq_table              4484  2 speedstep_ich,cpufreq_stats
orinoco_cs              8456  1 
orinoco                33932  1 orinoco_cs
hermes                  6912  2 orinoco_cs,orinoco
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
pcmcia                 24584  7 orinoco_cs
radeon                 68352  1 
drm                    58004  2 radeon
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
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
yenta_socket           22540  4 
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  0 
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0 
tpm_nsc                 6528  0 
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0 
intel_agp              21276  1 
agpgart                32328  2 drm,intel_agp
dm_mod                 50364  1 
joydev                  9280  0 
tsdev                   7616  0 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  0 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
3c59x                  37544  0 
mii                     5248  1 3c59x
uhci_hcd               28048  0 
usbcore               104316  2 uhci_hcd
ide_disk               16128  3 
ide_generic             1664  0 
piix                    9476  1 
ide_core              125268  3 ide_disk,ide_generic,piix
unix                   24624  64 
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

I don't know what any of that means

---

### Post by engla on 2006-02-12
There is a small tool called 'diff' that checks for differences between files. I used it on your module list:
```
$ diff -u3 mouse2 nomouse2
--- mouse2      2006-02-12 20:07:03.000000000 +0100
+++ nomouse2    2006-02-12 20:07:09.000000000 +0100
@@ -35,8 +35,8 @@
 ide_disk
 ide_generic
 intel_agp
-ipv6
 jbd
+joydev
 l2cap
 lp
 md

```
This suggest that if you startup without mouse, "joydev" is loaded extra. You could try starting up without mouse, using ctrl-alt-f1 to log in and type 'sudo rmmod joydev' and see if it fixes the issue. 

It could also be the other way around, that you need this driver, then try "sudo modprobe -v joydev" and see if that works..

ipv6 is about networking and shouldn't matter.. you could have started up in a different network environment and thus getting this difference.


[This post is mainly about checking and establishing what's wrong. I don't really know what's the best way to solve this. One thing could be checking what the file /etc/X11/xorg.conf says (post it if you like to), it partly handles trackpads.)

---

### Post by spurgetech on 2006-02-12
I tried both of the sugestions above, neither seemed to have any affect at all.
Here is the xorg.coonf file mentioned:
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by spurgetech on 2006-02-13
So from the lack of posts I guess no one realy knows the answer to this.:cry:

---

### Post by christhemonkey on 2006-02-14
Try adding these lines just under where it says HorizScrollDelta in your xorg.conf
```
    Option      "LeftEdge"     "1900" 
    Option      "RightEdge"    "5400" 
    Option      "BottomEdge"   "1800" 
    Option      "TopEdge"      "3900" 
    Option      "FingerLow"    "25" 
    Option      "FingerHigh"   "30" 
    Option      "MaxTapTime"   "180" 
    Option      "MaxTapMove"   "220" 
    Option      "VertScrollDelta" "100" 
    Option      "MinSpeed"     "0.02" 
    Option      "MaxSpeed"     "0.18" 
    Option      "AccelFactor"  "0.0010" 
```
Then later when it is talking about devices right at the end, swap the mouse and the touchpad round.
Just a thought!

---

### Post by spurgetech on 2006-02-15
Well, I tried that, but it did not work either. Anyother ideas out there. I read somewhere that I mat need a patch (ALPS I think) but could not figure how to install it.

---

### Post by m.musashi on 2006-02-15
I have a D610 at work that has ubuntu installed. As far as I can remember it has a working trackpad. I'm not sure if there is a mouse plugged in or not (I work in a school and it is checked out right now) but I don't think so.

If anyone can suggest where to look I can see how mine is set up to work and that might suggest a solution.

At least it's worth a try :).

EDIT: oops, I just noticed you have a **C** 610 and I have a **D** 610. I'm not sure what the difference is but maybe it's trivial.

---

### Post by spurgetech on 2006-02-22
Thanks M, If you could post your xorg.conf maybe I can copy what you got and get it to work on mine.
And if anyone else knows anything about this, I would love any ideas.

---

### Post by jjf on 2006-02-22
This page may help you:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

Scroll down to read the details about the Dell Latitude C600.  It sounds like it has power management and mouse issues like those you mention.  Being a Linux newbie myself, I can't provide too much help with exactly how to implement the fixes it mentions, but you could copy and paste them here and ask "how do I do this?!"

For example, when the guide says this:

> * APM works better than ACPI. Disable acpi at boot by adding 'acpi=off apm=on' to the kernel line in grub config. * Use the i8kmon package to monitor temperature and trigger fans

You can do this: 

- After boot up, hit CTRL-ALT-F1 to get a terminal.
- type **sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup**
(sudo means "superuser do" -- it lets you run things that Linux keeps you from for your own good; cp is "copy"; you're making a backup copy of the file in case you screw the original up)
- type **sudo nano /boot/grub/menu.lst** ("nano" is a text-editor that runs in the terminal -- you're saying "open this file in nano")
- Poke around in the menu.lst file and find the version of Ubuntu that automatically boots.  I think it's the top option.
- Indented underneath that top option, you'll find a line that says "kernel."  At the end of that kernel line, add **acpi=off apm=on**.

That should help with your power management issues, but the guy makes it sound like you need to manually trigger your fans when you notice the laptop's temps start to rise.  :(  

He also mentions the mouse problem, btw.

---

### Post by m.musashi on 2006-02-22
[QUOTE=spurgetech]Thanks M, If you could post your xorg.conf maybe I can copy what you got and get it to work on mine.
And if anyone else knows anything about this, I would love any ideas.[/QUOTE]
Oops, kind of forgot about this thread. Sorry. Here is a copy of my xorg.conf file. Don't know how useful it will be.

```
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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Maybe some of the gurus can figure it out.

EDIT: btw, I am using ubuntu on the Dell D610 right now without a usb mouse attached and the touchpad is working fine.

---

### Post by fireburns on 2006-02-28
That's odd...I'm using a C610 and don't experience this behavior.  Although I typically don't use the touchpad because mine went flaky.  I have changed some of my video settings in my xorg.conf, but the sections pertaining to our input devices are identical.

There is a mouse setting in bios...I'm assuming yours is TOUCHPAD-PS/2 MOUSE?  I have mine set to PS/2 so it will diable the touchpad when I plug a PS/2 mouse in....

I'm sorry I can't be more helpful, but this does seem to indicate a software issue somewhere, rather than a C610-specific problem.

---

### Post by m.musashi on 2006-02-28
If you are referring to my xorg.conf, it is the one that works. I posted it so that spurgetech might be able to find out why his isn't working. Good to know that the two are identical. Maybe he will be able to use the info to get his running.

---


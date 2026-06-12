---
title: "please help me install ATI drivers!!!"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by xflbret on 2007-05-02
All I want is video drivers installed...does that make me a bad guy? Sorry, just frustrated...a lot.

Anyway, here's what I got...I am new to Ubuntu, and even newer to my laptop which I bought yesterday. It is a Dell Latitude D600 with an ATI Mobility Radeon 9000 video chip (which has 32 megs of ram). From what I got from ATI's site, I am supposed to be using the 8.28.8 driver, since that's the latest one that supports my chip. I am running 7.04, which I installed clean. 

I could tell you what I've done so far in detail, but to be honest I have been so frustrated I haven't kept good track. What I can tell you is, even with installing Envy, I either get to the point where the xserver wont start, or I can't even get that far because ubuntu tells me a command is bad, despite the fact that I am copying and pasting right from the directions I'm reading. I want to stay a little vague so I can try everything suggested to me, just in case I missed a step or fatfingered something in my previous attempts.

Thanks for letting me vent, and thanks in advance for the help.

---

### Post by bobplano on 2007-05-02
are you installing fglrx or open source drivers? try this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by ammu on 2007-05-02
i suffered a lot  try my way i tried envy and all other methods just missed this. anyway check this post
[http://ubuntuforums.org/showpost.php?p=2569670&postcount=185](http://ubuntuforums.org/showpost.php?p=2569670&postcount=185)
   or read that thread thoroughly .hope it will help/

---

### Post by xflbret on 2007-05-02
> **bobplano said:**
> are you installing fglrx or open source drivers? try this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

when i tried the open source i got to the point where I couldnt start the xserver. I believe it said the problem was "no screens found", even though there were in the xorg file. while at a command prompt, I tried running fglrxinfo, and I forgot the exact error message (sorry), but I didnt get any info, it was more like module not found or something.

When I tried to install the binary drivers, everytime i tried to run the bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/feisty  command (changing the number for my driver version of course) i always got not found or cant be run or something of that nature. I tried running it starting with sh and bash, and didn't get anywhere. 

I cant use these instructions anyway, they both include a step I can't perform. Remember Star Trek 6 when Scotty told Spock "A computer doesn't lie?" Well, Scotty didn't use 7.04 on his computer. I go to system > administration > restricted drivers manager, and I get "your hardware does not need any restricted drivers"

---

### Post by xflbret on 2007-05-02
> **ammu said:**
> i suffered a lot  try my way i tried envy and all other methods just missed this. anyway check this post
[http://ubuntuforums.org/showpost.php?p=2569670&postcount=185](http://ubuntuforums.org/showpost.php?p=2569670&postcount=185)
   or read that thread thoroughly .hope it will help/

well, i tried that,and it seemed to go ok, but there was no effect, positive or negative. i want to run 3d acceleration so i can run beryl, but more importantly, i want to change resolution. i am at 1400x1050 right now. there are other resolutions available to me, but when i choose then they dont take. the screen goes black for a few seconds, then it goes back to the 1400 resolution. everything is too small. i would much prefer 1024 or 1152.

---

### Post by ammu on 2007-05-02
what is output of fglrxinfo?
and what about fps you getting now?
type glxgears in terminal and wait for 5 econds it output your fps....

---

### Post by xflbret on 2007-05-02
i uninstalled the fglrx as I was following the directions on the following page...

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

but that also got me pretty much nowhere.

as far as the glxgears goes, here's what I got...

bret@blaine:~$ glxgears
4304 frames in 5.0 seconds = 860.663 FPS
4300 frames in 5.0 seconds = 859.930 FPS
4301 frames in 5.0 seconds = 860.133 FPS
4295 frames in 5.0 seconds = 858.865 FPS
4302 frames in 5.0 seconds = 860.319 FPS
bret@blaine:~$

---

### Post by ammu on 2007-05-02
did you add these lines ? in xorg.conf
 Section "Extensions"
        Option  "Composite" "Disable"
EndSection

? can you try  link which i gave above ?
[http://ubuntuforums.org/showpost.php?p=2569670&postcount=185](http://ubuntuforums.org/showpost.php?p=2569670&postcount=185)
               i tried before doing that almost every method that i googled but on fresh install without touching anything that works great.
              after that my fps are  
46075 frames in 5.0 seconds = 9214.898 FPS
44939 frames in 5.0 seconds = 8987.788 FPS
42935 frames in 5.0 seconds = 8586.845 FPS
45193 frames in 5.0 seconds = 9038.548 FPS
45329 frames in 5.0 seconds = 9065.666 FPS
44653 frames in 5.0 seconds = 8930.527 FPS

---

### Post by sad_iq on 2007-05-02
It seems no one suggested...but could you paste the content of *xorg.conf*....maybe we can see something there...and also paste the output from **lsmod**!!!

---

### Post by xflbret on 2007-05-02
here is output from lsmod

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_centrino      9920  0 
cpufreq_ondemand        9228  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
freq_table              5792  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
ac                      6020  0 
button                  8720  0 
dock                   10268  0 
video                  16388  0 
asus_acpi              17308  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
backlight               7040  1 asus_acpi
battery                10756  0 
ipv6                  268704  8 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
pcmcia                 39212  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
joydev                 10816  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ipw2100                72244  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
ieee80211              34760  1 ipw2100
ieee80211_crypt         7040  1 ieee80211
yenta_socket           27532  4 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
serio_raw               7940  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
psmouse                38920  0 
intel_agp              25116  1 
agpgart                35400  2 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  4 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
ata_generic             9092  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
tg3                   109700  0 
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
bret@blaine:~$ 

here is my xorg.conf file, my latest one anyway

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
##
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
	Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by Ash1984 on 2007-05-02
I am having a similar problem. Xserver will not start. I'm fairly confident my xorg.conf contains the same information as yours except I have:

Options "Composite" "false"

I am running Ubuntu 7.04 on a Tecra S1 with ATI Radeon Mobility 9000 graphics.

Xserver reports an error on boot up:

(EE) No devices detected.

Fatal server error:
no screens found

I followed the instructions at:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I'm 100% sure I had success installing proprietary drivers when running under 6.10. Also Xserver wouldn't start when I upgraded to 7.04. That makes it seem like a problem with 7.04.

All I really want to do is revert back to the Open Source drivers so I can get my uni dissertation (I can live without wolfenstein for now) but I can't find how to revert on the website.

---

### Post by miggols99 on 2007-05-02
You could try changing
```
Section "Device"
 Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
 Driver "ati"
 BusID "PCI:1:0:0"
 Option "XAANoOffscreenPixmaps"
 EndSection
```
to
```
Section "Device"
 Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
 Driver "vesa"
 BusID "PCI:1:0:0"
 Option "XAANoOffscreenPixmaps"
 EndSection

```
So you can at least get X running.

---

### Post by Ash1984 on 2007-05-02
Making those changes seemed to have no effect. I still receive the same error message.

---

### Post by Ash1984 on 2007-05-02
Xflbret, my xorg.conf file is now identical to yours and X Server now successfully starts. The only difference is my serverlayout section is at the start of the file. I'm not sure how much of a difference that would make.

---

### Post by tyboon on 2007-05-02
They say that beryl with fgrlx usually crashes..
i am running Beryl with Ati 9600 series in xGL gnome...It is running ok ..no problems at all..If you havent find a solution i will write to you a full  install procedure..I hope it will work on your desktop too..
Just send me a message...let me know...
:guitar:

---

### Post by tyboon on 2007-05-02
> well, i tried that,and it seemed to go ok, but there was no effect, positive or negative. i want to run 3d acceleration so i can run beryl, but more importantly, i want to change resolution. i am at 1400x1050 right now. there are other resolutions available to me, but when i choose then they dont take. the screen goes black for a few seconds, then it goes back to the 1400 resolution. everything is too small. i would much prefer 1024 or 1152.
Reply With Quote 
try thyis command for resolution :

 sudo dpkg-reconfigure -phigh xserver-xorg

Pick Ati with enter...pick resolution with the space button -> press enter to exit

---

### Post by xflbret on 2007-05-02
just for fun, I again ran the ati installer via envy to give it another chance. but, i know it's going to fail. i havent restarted yet. i thought i would post my xorg.conf file first.


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
##
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
	Option	    "AIGLX" "true"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver      "ati"
	Option	    "XAANoOffscreenPixmaps"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1400x1050" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

### Post by tyboon on 2007-05-03
I am seeing that you use a fgrlx driver....Have you tried typing the command on terminal and pick the regular ATI driver?

---

### Post by xflbret on 2007-05-03
> **tyboon said:**
> try thyis command for resolution :

 sudo dpkg-reconfigure -phigh xserver-xorg

Pick Ati with enter...pick resolution with the space button -> press enter to exit

i tried this several times. I tried the ati and the vesa driver with several different resolutions with no results. either the xserver wouldnt start or i would boot to a black screen. i had to restore a backup of xorg.conf to get rolling again.

---

### Post by xflbret on 2007-05-03
> **tyboon said:**
> I am seeing that you use a fgrlx driver....Have you tried typing the command on terminal and pick the regular ATI driver?

i was unable to do that, also. i cant remember why, but i will try again when i get home tonight and try again

---

### Post by xflbret on 2007-05-04
ok, i tried installing ati's 8.28.8 drivers, and i was unsuccessful. here's what i get

./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

i have searched these forums for that error message, and the only thing i could learn is that i'm not alone. there's got to be some solution, i know it

---

### Post by tyboon on 2007-05-04
well....
i ll send you o message with the whole thing...install beryl etc..reposiotries..etc...
I hope that it will work...the only thing is that you messed your conf a bit..
I am just a novice too tryin to get a grip on linux interface..i ll give you my best an hope it will work..
:-({|=

---

### Post by bobplano on 2007-05-04
try```
sudo sh ati-installer.sh
```
i don't know if that will work but i think .sh files need to be run with sh command

---

### Post by tyboon on 2007-05-04
Here it goes...

First of all open the terminal and type...

> code: sudo gedit /etc/apt/sources.list 

and copy this to sources list. :

> ## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
# deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
# deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17
# deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
 

Paste -> save -> close
 
 In this list is included the free beryl-project org and the medibuntu...Ignore the applet sayin that it has to upgrade for the time being...Go to System --> Administration --> Synaptic.
There just do that a) Reload, b) Mark All Upgrades c) Apply.

In case you get GPG errors it might be from the medibuntu...just type this in to terminal..
 > wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
 and for beryl type this... > wget -q [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release/_PUBKEY 3FF0DB166A7476EA -0- | sudo apt-key add -

Now type >  sudo apt-get update
It should update normally now....
Do this stapes and let me know...I ll give you the rest later..just in case something goes wrong..Post here..
I hope it will work till here

---

### Post by xflbret on 2007-05-04
> **bobplano said:**
> try```
sudo sh ati-installer.sh
```
i don't know if that will work but i think .sh files need to be run with sh command

no good. still the stupid bad substitution error

---

### Post by tyboon on 2007-05-05
if still you got problems try this...
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Its a driver named ENVY for Ati chipsets  that most users use...
I hope it will help you....

---

### Post by xflbret on 2007-05-06
well, i found a solution...i went back to 6.10. 7.04 was released prematurely. i wish i never tried to install it on my laptop or upgrade my desktop. now that I have 6.10 it works fine

---

### Post by xflbret on 2007-05-18
ok, I got frustrated with it for a while, but I am back in it again. I really cant accept its impossible to get my video working as it should with 7.04. So here's what I did...

i installed the fglrx driver with method 1 listed in the following link

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

i know it says it supports 9500+, and i only have the 9000. but what else can I do? I got the ati radeon mobility 9000, I want to have 7.04, there's got to be something i can do here. anyway, this didnt work. the xserver wouldnt start. it told me no screens found (I think). anyway, I saved the xorg.lies file, oops, i mean xorg.conf file that caused x not to start. here it is..


# /etc/X11/xorg.conf (xorg X Window System server configuration file the lies)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by xflbret on 2007-05-18
I gotta say this makes me pretty angry. I have to upgrade my hardware to upgrade to the latest OS? What is this, Vista? This ain't right. Why in the world would the ATI drivers work just fine in 6.06 but give troubles in 6.10 and not work at all in 7.04? Makes no sense.

---

### Post by lazyart on 2007-05-18
New version of X server in Feisty and the ATI drivers for the 9000 don't support it.

---


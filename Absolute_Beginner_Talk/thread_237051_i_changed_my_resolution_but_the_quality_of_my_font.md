---
title: "i changed my resolution but the quality of my fonts are worse!! please help me"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by SkippyJames on 2006-08-15
i changed my resolution from 1024x768 to 1280x800, but the quality of the fonts are worse now. Can some one help me about these please. 

Thanks a lot

---

### Post by Tom Brokaw on 2006-08-15
Try this:
[http://www.ubuntuforums.org/showthread.php?t=4456&highlight=fonts+smooth](http://www.ubuntuforums.org/showthread.php?t=4456&highlight=fonts+smooth)

---

### Post by coffeecat on 2006-08-15
1024x768 is 4x3 ratio standard monitor format. 1280x800 is widescreen. If your monitor is not widescreen I should imagine you'll get some odd effects if you run it with a widescreen resolution. I wouldn't have thought this is possible.

Have you changed your monitor? What is it's optimum resolution?

**Edit:** I'm posting this from a widescreen laptop at 1280x800 - it's optimum resolution. Out of interest I looked in System > Preferences > Screen Resolution and I see that it is offering me 1024x768 as well. I won't try this because 1024x768 is simply not suitable for this lcd and I'd get a distorted image. I can't understand why two different ratio resolutions are being offered - I should think this is a bug.

---

### Post by szf on 2006-08-16
I have to admit that I was sceptical that a saving small xml stanza as $HOME/.fonts.conf would make a difference. I was wrong! Thank you Ubuntu Community! Firefox finally looks as good as on my FC5 install.

Additional options tried previously (additive overall, nothing taken back):

In /etc/X11/xorg.conf:
Section "Device"
...
 Option          "UseEdidDpi" "false"
 Option          "Dpi" "96 x 96"
...
EndSection
Section "Monitor"
...
 DisplaySize     338     271 # <dimension>/96 * 25.4 i.e. 1280/96 * 25.4; 1024/96 * 25.4
...
EndSection

---

### Post by coffeecat on 2006-08-16
> **szf said:**
> I have to admit that I was sceptical that a saving small xml stanza as $HOME/.fonts.conf would make a difference. I was wrong! Thank you Ubuntu Community! Firefox finally looks as good as on my FC5 install.

**szf**, you've mentioned something I feel very strongly about. Putting that stanza in ~./.fonts.conf switches on autohinting which I much prefer as well. A couple of months ago Automatix did that for me (calling it 'smoother fonts') but then I read in the Automatix forum that they had withdrawn the feature because some people didn't like it. Well, what about the people who do like it? I think that is a lamentable attitude. So I did some research. The stanza is probably the same as you will find in /etc/fonts/conf.d/autohint.conf so you could also copy that to ~./.font.conf instead. By doing that you only get autohinting switched on for the particular user. To switch it on system-wide either do:

```
sudo dpkg-reconfigure fontconfig
``` in a terminal. Choose autohinting with the first questions and the defaults for the next two.

Or:

```
sudo cp /etc/fonts/conf.d/autohint.conf /etc/fonts/conf.d/10-autohint.conf
``` 
Restart the X-session each time. If you want to remove autohinting, merely delete ~./.font.conf or 10-autohint.conf (whichever you chose), or if you ran dpkg-reconfigure, run it again and switch off autohinting.

Autohinting doesn't just smooth out characters, it changes the relative shapes and sizes of verticals, horizontals and curves in individual letters. Compare the appearance of a font such as Verdana with and without autohinting and with how it appears in Fedora. Quite a revelation.

---

### Post by SkippyJames on 2006-08-16
sorry for the late answer,

I have a 15.4 TFT screen on my laptop at asus.com it says wxga 1280x800 is supported so that's why i changed it but the fonts couldn't keep up with me i guess. I turned on auto-hinting and there was an improvement but not as good as they looked on 1024x768. 
Thank you all for your ideas, i will try them when i get home to my ubuntu,(i am now at work in microsoft :)). 

Thank you all 

P.s. i also somehow lost the virtual terminal (ctrl + alt + f[1-6]). if anyone knows why that would be great too.

---

### Post by coffeecat on 2006-08-16
**SkippyJames**, I've had another idea. If your laptop manufacturer says that 1280x800 is supported, then your lcd must be a widescreen one and 1024x768 would give a distorted image. Yet you say the fonts look better. What is your graphics card/chipset? Is it an ATI one? The reason I ask is that, in my experience, font rendering with an ATI card using the open source graphics driver is distinctly appalling. Perhaps using the wrong resolution tidies it up. ???

When starting threads you can help yourself by giving relevant details of your hardware so that others can give appropriate advice. So - what make/model of laptop do you have? Is it widescreen? What is the graphics card/chipset? What software driver are you using? :wink:

---

### Post by SkippyJames on 2006-08-16
Yes i knew i forgot something, i have an asus a6jc laptop with widescreen, and have nvidia 7300 go. And my chipset is intel 945. I downloaded the nvidia-glx package from synaptics. And yes the funny thing is even without changing the font rendering settings the fonts looked better in 1024x768 resolution. 

But does anyone know if i should download it again after changing the resolution. 

Thanks again for all your help

---

### Post by SkippyJames on 2006-08-16
I tried them but it didn't work the fonts still look bad. Maybe i should try automatix.

Thanks anyway.

---

### Post by smurphv2 on 2006-08-16
hey all,
   I'm using a Dell XPS M1210, which has a resolution of 1280x800 in windows. It is a widescreen. I am inserting my xorg.conf at the bottom of this. I have not edited it at all, but it appears to have 1200x800 in there. However, when I go to System > Preferences > Screen Resolution, my only option is 1024x768. Anyone have any ideas on how to change to 1280x800?

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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by SkippyJames on 2006-08-16
hey,

i had the same problem. i solved it by adding these lines to the xorg.conf under Section "Monitor":
HorizSync       31.0 - 81.0
VertRefresh     56.0 - 75.0

however these values are specific to my monitor, you should research yours from the net
(you can use google just enter the model/maker of the monitor and search for specs after you find a page).

While adding or changing this settings make sure you backup your xorg.conf 
backup command is : sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
if you enter values that your screen dont support you may lose the gui. And you would have to restore.

I hope i could help

---

### Post by Markus Valkeapaa on 2006-08-17
smurphv2,
"915Resolution" by Steve Tomljenovic helped me to get 1280x800 resolution in Dell Inspiron 700m problem. See [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) for details and download. This is usefull if your display uses certain Intel chipsets (from the site: "845G, 855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets")
-Markus

---

### Post by coffeecat on 2006-08-17
**SkippyJames**, sorry I haven't been able to get back before. I'm sure you know that you have to do more than download the nvidia-glx package to get the proprietary 'nvidia' driver working. Slightly different instructions are [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper"), or [here]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29"), or [here]("http://www.ubuntuforums.org/showthread.php?t=131267&highlight=nvidia"). Or you could use Automatix.

I've found that Nvidia with the proprietary driver gives the best font rendering of all that I have tried. Font rendering with the 'nv' OS driver is not as good, but not nearly as bad as with ATI and OS driver. So if you do have the proprietary 'nvidia' driver installed I have no other suggestions.

---

### Post by smurphv2 on 2006-08-17
> **Markus Valkeapaa said:**
> smurphv2,
"915Resolution" by Steve Tomljenovic helped me to get 1280x800 resolution in Dell Inspiron 700m problem. See [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) for details and download. This is usefull if your display uses certain Intel chipsets (from the site: "845G, 855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets")
-Markus

Markus,
   How did you get this to start up on boot? I didn't see any /etc/init.d/boot.local file. I tried adding it in system > preferences > sessions > startup programs "/usr/bin/915resolution 38 1280 800" but that doesn't seem to have worked. Thanks.

---

### Post by smurphv2 on 2006-08-17
using apt-get install 915resolution solved this for me. Thanks

---

### Post by bsawler on 2007-06-18
Hi all, 

I just load linux for my first time.  I am trying to set my resolution to 1280x1024 but I am struggling.  I am new to linux so coding etc I can do is only what I read in these forums etc. 

I installed and set the resolution with 915resolution on several different modes.  When I reboot the system I get 6 options from the previous 3 default after installation of ubuntu, but none of these six are the one I want.  

I ran ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and selected the resolution above and I also ran ```
sudo dpkg-reconfigure xserver-xorg
``` and selected the resolution above.  Rebooted but still cannot get my required resolution.  

My chipset is 865G. I was going to run the auto915 from [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/).  But this link is broken and on the following page [http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html) the download page is broken.  

I am running out of options.  Any insight would be greatly appreciated. 

Regards,
BS

---


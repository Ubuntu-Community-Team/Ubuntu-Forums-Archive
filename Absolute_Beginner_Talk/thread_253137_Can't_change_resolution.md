---
title: "Can't change resolution"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-09-07
i am unable to change my screen resolution from 1400x1050. Anytime i do this my screen blacks and then jumps back to 1400x1050. i have an ATI Mobility Radeon 9000. Any suggestions?

---

### Post by halitech on 2006-09-07
do you have the ATI drivers installed?

[http://www.ubuntuforums.org/showthread.php?t=221320&highlight=radeon+9000]("http://http://www.ubuntuforums.org/showthread.php?t=221320&highlight=radeon+9000")

---

### Post by swp6499 on 2006-09-07
i think i have whatever the default drivr is for this card is installed when u install ubuntu but im not sure. how can i tell which driver? and i think my friend has tried with the fglrx driver and the ati driver and it still wont change??

---

### Post by halitech on 2006-09-07
are you making the change by going to 

System - Preferences - screen resolution?

---

### Post by renesisspeed on 2006-09-07
I had a similar problem with my laptop, and was able to change the resolution by editing the xorg.conf file

[http://www.ubuntuforums.org/showthread.php?p=1475114#post1475114](http://www.ubuntuforums.org/showthread.php?p=1475114#post1475114)

My problem was the opposite of yours though as my res was too low
but maybe it will help

---

### Post by swp6499 on 2006-09-07
i personally tried to change it in settings-screen resolution. my friend tried to edit the xconnf file for the resolution although im not sure what he did. im newer to ubuntu been using it for about 4 months now. so im unsure about editing things in xconf but no matter what we tried no other screen resolutions worked other than 1400x1050 and this is frustrating when trying to get certain things to work. should i be trying something other than settings-screen resolution?

---

### Post by halitech on 2006-09-07
from a post here:

[http://www.ubuntuforums.org/showthread.php?t=253146&highlight=resolution]("http://www.ubuntuforums.org/showthread.php?t=253146&highlight=resolution")

Open terminal and copy and paste command below:

sudo dpkg-reconfigure xserver-xorg

And select which res's you want

---

### Post by swp6499 on 2006-09-07
when i do this it asks me several questions about my card and keyboard etc...when i get to the keyboard it tells me to leave something blank and when i do it keeps asking me over and over again and never moves on??

---

### Post by halitech on 2006-09-07
should be able to select the defaults until it gets to the resolutions you want to use. what exactly is it asking that it won't go past?

---

### Post by swp6499 on 2006-09-07
&#9474; For the X server to handle your keyboard as you desire, keyboard options
 &#9474; may be entered.  Available options depend on which XKB rule set was       &#9618;
 &#9474; previously selected.  Not all options will work with every keyboard       &#9618;
 &#9474; model and layout.                                                         &#9618;
 &#9474;                                                                           &#9618;
 &#9474; For example, if you wish the Caps Lock key to behave as an additional     &#9618;
 &#9474; Control key, you may enter "ctrl:nocaps"; if you would like to switch     &#9618;
 &#9474; the Caps Lock and left Control keys, you may enter "ctrl:swapcaps".       &#9618;
 &#9474;                                                                           &#9618;
 &#9474; As another example, some people prefer having the Meta keys available on  &#9618;
 &#9474; their keyboard's Alt keys (this is the default), while other people       &#9618;
 &#9474; prefer having the Meta keys on the Windows or "logo" keys instead.  If    &#9618;
 &#9474; you prefer to use your Windows or logo keys as Meta keys, you may enter   &#9618;
 &#9474; "altwin:meta_win".  

but when i leave it blank like it says is ok it goes back to the screen above over and over

---

### Post by bodhi.zazen on 2006-09-07
> **swp6499 said:**
> when i do this it asks me several questions about my card and keyboard etc...when i get to the keyboard it tells me to leave something blank and when i do it keeps asking me over and over again and never moves on??

You can learn X later, for now you are making it more complicated then it has to be.

Use:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
re-configures X (re-writes xorg.conf, saves a back up of original). -phigh skips all options but but resolution.

---

### Post by swp6499 on 2006-09-07
i went through the whole process and set my screen resolution to 1024x768 which is what i want and it still blacks out. any ideas past this?

---

### Post by swp6499 on 2006-09-07
when i type this 

sudo dpkg-reconfigure -phigh xserver-xorg

into terminal i get this 

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20060907230437
 
no settings for resolution?

---

### Post by acorn22 on 2006-09-07
I take it your on a laptop?

and does this happen in gnome and KDE? or have you only used gnome? (The brown/orange one)

---

### Post by swp6499 on 2006-09-07
and my refresh rate is at 62 hz and cant change that either?

---

### Post by bodhi.zazen on 2006-09-07
Duplicate Post, see below...

---

### Post by bodhi.zazen on 2006-09-07
> **swp6499 said:**
> i went through the whole process and set my screen resolution to 1024x768 which is what i want and it still blacks out. any ideas past this?

If sudo **dpkg-reconfigure -phigh xserver-xorg** does not work,

```
sudo nano /etc/X11/xorg.conf
```

Edit the default depth line, change from 24 to 16;
```
Section "Screen"
    Identifier  "XXX"
    Device      "XXX"
    Monitor     "XXX"
    DefaultDepth **16**......
```

Note: I XXX out some information, ovbiously DO NOT EDIT THESE LINES!

Then Ctrl-X to exit, "Y" to save edit.

Restart X: Ctrl-Alt-Backspace

---

### Post by swp6499 on 2006-09-07
i have tried in both ubuntu and kubuntu and neither will change resolution or refresh rate?

---

### Post by swp6499 on 2006-09-07
i tried this

 Originally Posted by swp6499  View Post
i went through the whole process and set my screen resolution to 1024x768 which is what i want and it still blacks out. any ideas past this?

If sudo dpkg-reconfigure -phigh xserver-xorg does not work,

Code:

sudo nano /etc/X11/xorg.conf


Edit the default depth line, change from 24 to 16;
Code:

Section "Screen" Identifier "XXX" Device "XXX" Monitor "XXX" DefaultDepth 16......


Note: I XXX out some information, ovbiously DO NOT EDIT THESE LINES!

Then Ctrl-X to exit, "Y" to save edit.

Restart X: Ctrl-Alt-Backspace

and it still wont set my resolution to anything other than 1400x1050??

---

### Post by bodhi.zazen on 2006-09-07
Well, no time like the present then.

You will need to google your monitor and find the vertical and horizontal refresh rates. Try you make and model # with vertical refresh in the search line.

Once you know this, enter them here:
[sudo nano /etc/X11/xorg.conf]
> Section "Monitor"
    Identifier  "display_sgi"
    VendorName  "sgi"
    ModelName   "gdm20e21"
    HorizSync   30-96 **ENTER YOU #'s**
    VertRefresh 50-160 ** ENTER YOUR #'s**
    Option      "DPMS"

and enter your desired resoulution on these lines:
>     Subsection "Display"
        Depth       16
        Modes       "1600x1200" "1280x1024" "1024x768" "800x600"
    Subsection "Display"
        Depth       24
        Modes       "1600x1200" "1280x1024" "1024x768" "800x600"

---

### Post by swp6499 on 2006-09-08
im using a laptop and the monitor detected says generic monitor..anyway to find out who manufactured this monitor..its a dell inspiron 600m from aug 2003...

---

### Post by bodhi.zazen on 2006-09-08
I found ths xorg.conf for BSD on a "Dell Latitude C600"

You could try editing your xorg.conf using this as a template. It will likely not work to cut and paste the entire file.

The most important sections are "monitor" and "screen"

```
xorg.conf:
Section "Module"
# Double Buffer Extension module
Load "dbe"

# Direct Rendering Interface modules
#Load "glx"
#Load "dri"

# Font modules
Load "type1"
Load "freetype"
#Load "xtt"
#Load "speedo"

SubSection "extmod"
Option "omit xfree86-dga" # don't initialise the DGA extension
EndSubSection
EndSection

Section "Files"
RgbPath "/usr/X11R6/lib/X11/rgb"
FontPath "/usr/X11R6/lib/X11/fonts/misc/"
FontPath "/usr/X11R6/lib/X11/fonts/TTF/"
FontPath "/usr/X11R6/lib/X11/fonts/Type1/"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi/"
#FontPath "/usr/X11R6/lib/X11/fonts/100dpi/"
#FontPath "/usr/X11R6/lib/X11/fonts/CID/"
#FontPath "/usr/X11R6/lib/X11/fonts/local/"
#FontPath "/usr/X11R6/lib/X11/fonts/Speedo/"
#FontPath "/usr/X11R6/lib/X11/fonts/TrueType/"
#FontPath "/usr/X11R6/lib/X11/fonts/freefont/"
#ModulePath "/usr/X11R6/lib/modules"
EndSection

Section "InputDevice"
Identifier "main_keyboard"
Driver "kbd"
Option "AutoRepeat" "500 30"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "pl"
EndSection

Section "InputDevice"
Identifier "touchpad"
Driver "mouse"
Option "Protocol" "Auto"
Option "Device" "/dev/sysmouse"
EndSection

Section "Monitor"
Identifier "dell_lcd_screen"
Option "DPMS"
HorizSync 31.5-68
VertRefresh 50-85
Modeline "1024x768-85" 94.39 1024 1088 1200 1376 768 769 772 807 -HSync +Vsync
EndSection

Section "Screen"
Identifier "main_screen"
Device "ati_rage_128"
Monitor "dell_lcd_screen"
DefaultDepth 16
Subsection "Display"
Modes "1024x768-85"
ViewPort 0 0
EndSubsection
EndSection

Section "Device"
Identifier "ati_rage_128"
Driver "r128"
VideoRam 8192
Option "AGPMode" "2"
EndSection

Section "ServerLayout"
Identifier "main_layout"
Screen "main_screen"
InputDevice "touchpad" "CorePointer"
InputDevice "main_keyboard" "CoreKeyboard"
EndSection
```

[BSD Forums](http://www.bsdforums.org/forums/archive/index.php/t-15439.html)

It is a long page, look near the very bottom of the page or search the page for "Dell" :twisted:

---

### Post by swp6499 on 2006-09-08
for some reason it won't let me in to edit my xorg.conf maybe in doing it wrong can u give me command line to get into this file please

---

### Post by bodhi.zazen on 2006-09-08
Try:
```
gksudo gedit /etc/X11/xorg.conf
```

or if you prefer a terminal:
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by swp6499 on 2006-09-08
whenever i type this in i get a blank file nothing in it??

---

### Post by bodhi.zazen on 2006-09-08
Either it is a typo on your part or xorg.conf was deleted.

Can you find xorgconf with nautilus (browse to /etc/X11)?
Size of file?

In a terminal type:
```
sudo cat /etx/X11/xorg.conf
```
you should see the contents of xorg.conf flash by in the terminal.

If the file is blank, you are back to:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
which will re-write xorg.conf, which you can then edit.

---

### Post by swp6499 on 2006-09-08
ok i found out my monitor is manufactured by dell its a 14.1 inch sxga but i cant find any info about what my refresh rates are. i did however see somewhere where it said the maximum refresh rate was 60hz which i find odd because mine is currently set at 62. also i did get my xorg.conf file back but i need to know what i need to put in it any help?? thanks for all ur help so far

---

### Post by swp6499 on 2006-09-08
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
	Option		"XkbOptions"	"default"
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
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
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


thought maybe this would help also

---

### Post by swp6499 on 2006-09-08
any more suggestions please?

---

### Post by bodhi.zazen on 2006-09-09
Posting your xorg.conf was very helpful.

You need to add to the "monitor" section to include your monitor's refresh rates.

I searched Dell and the Dell forums, but I do not know what they are.

Perhaps you could contact Dell and ask?

Current corg.conf:
> Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Needs to read something like this:
> Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31.5-68 **# I do not know the values for your monitor.**
VertRefresh 50-85 **# I do not know the values for your monitor.**
EndSection

My only other thoughts would be to try booting a Linux Live CD that works with your monitor and looking up these values in the live version's xorg.config.

This will still be located in /etc/X11/xorg.conf even though it is a live CD.

Suggestions: knoppix, mepis, pclinux, xandros

---

### Post by swp6499 on 2006-09-11
sorry been outta town since yesterday...gonna try knoppix tomorrow and see if it detects refresh rates....thanks for ur help so far and ill get back to ya and let  u know

---

### Post by swp6499 on 2006-09-11
ok the knoppix 4.0 live cd wont run because of my resolution...and it wont let me change it on the live cd to 1400x1050 to run it which wouldnt seem to matter anyway because id be in the same boat as i am with ubuntu...this is killing me

---


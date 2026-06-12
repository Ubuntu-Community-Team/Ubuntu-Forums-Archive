---
title: "Intel Graphics Card.. and some other questions"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Winnie the Pooh on 2006-12-04
Hi everyone; I'm quite new to Ubuntu; had a little bit of fun playing around with it, better than Windows in many ways :-D but (ahhh, it's always the "but") I just have a few questions...
1) My computer is OLD (4 years old); I wonder how can I update the drivers for my hardware? In Windows I can go into Control Panel and update the drivers, but how do I do that in Ubuntu? Because I really don't know how to install them from the company websites....
2) I looked around the websites and this forum for information on my graphics card: 82845G/GL[Brookdale-G]/GE Chipset by Intel, and did not really find anything; I'm wondering if it'll still support all the visual things like Beryl and not crash? (When I tried to install Edgy by putting the Live-CD into the CD-ROM, the whole thing crashes; I can access the menu to choose "Install Ubuntu", but after that, there's no splash screen, and I only see a tiny faint cursor on the upper-left corner of my screen, then the screen kind of flashes, with numerous horizontal lines across the screen, and freezes. Is this related to my graphics card? I'm kind of worried....)
3) A minor question... all the word files I create using Open Office 2 (the one that came with Dapper) and saved in .rtf format will open in Microsoft Office, but with all the paragraphs and fonts and spacings and indents messed up. Is there a way to fix this... or do I have to save in some other format?
Terribly sorry for these long questions. MANY MANY THANKS in advance!!! ;)

---

### Post by endersshadow on 2006-12-04
Well hello there, Winnie.  Loved you when I was a kid.  Anyway...

1. Without going into the real deep down stuff about Linux and drivers, let's just say it's a bit different than in Windows in terms of handling hardware.  I'm assuming you're referring to how it's a bit blurry and the like (which gets *really* annoying).  I, too, have an older compy (3 years or so), and have the same graphics card as you.  So, here's what you do, my friend:

[LIST]
[*] Open up a terminal (Applications>Accessorites>Terminal)
[*] Type this in:
```
sudo apt-get install 915resolution
```
[*] Once that installs, type this in the terminal:
```
sudo 915resolution -l
```

You'll get a printout that reads like so:
```
eric@homesteadgrays:~$ sudo 915resolution -l
Password:
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 2
Mode Table Offset: $C0000 + $36f
Mode Table Entries: 21

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1400x1050, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1400x1050, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1400x1050, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 7c : 1024x600, 8 bits/pixel
Mode 7d : 1024x600, 16 bits/pixel
Mode 7e : 1024x600, 32 bits/pixel
```

Find a mode with the resolution and the color depth that you aren't going to use. For example, I'm never going to use 800x600, 16 bit/pixel, which is Mode 43.

Know what resolution you're going to use (in my case, 1400x1050), and your depth (you're probably going to want 32).

Knowing that...
[*] Type this command:
```
sudo 915resolution 43 1400 1050 32
```
Where 43 is the mode previously mentioned, 1400 is your resolution width, 1050 is the resolution height, and 32 is your color depth.  Change those numbers as you see appropriate.

[*] Log out and log back in.  Life will be peachy.
[/LIST]

2. Yes you can get Beryl! I use it and love it!
Here's how:

[LIST]
[*] In that same terminal, type this command:
```
sudo gedit /etc/apt/sources.list
```

Gedit will pop up with a document loaded.

[*] At the end of that document, add these lines:
```
#Beryl
deb http://ubuntu.beryl-project.org/ edgy main
```

[*] Save and close the document

[*] In the terminal, type:
```
sudo apt-get update
sudo apt-get install beryl
```

Beryl and all of its components will then be installed.

[*] Then, go to System>Preferences>Sessions, and go to the Current Session tab

[*] Find the entry that says metacity.  It will have a two arrow circle next to it. Select it by single clicking on it.

[*] In the Style drop down box, change it from Restart to Normal

[*] In the Startup Programs tab, click the add button and type in emerald. Next, add beryl.  You can close the Sessions window after this.

[*] Back in the terminal, type this:
```
killall metacity
emerald &
beryl &

```

It will first remove the borders from your windows (don't freak out), and then replace them with the beautiful Beryl borders! To change preferences, go to System>Preferences>Beryl Settings.

[*] PLAY AND HAVE FUN!

[/LIST]

3. Try opening them in Open Office and saving them as Microsoft Word 2000/XP (.doc).  Then go back to Word and see what you get.

Hope this helps!

---

### Post by bodhi.zazen on 2006-12-04
endersshadow: Nice post 8)

---

### Post by IYY on 2006-12-04
> My computer is OLD (4 years old)

4 years is considered old these days? I have an 8 year old machine I'm perfectly happy with...

---

### Post by endersshadow on 2006-12-04
> **IYY said:**
> 4 years is considered old these days? I have an 8 year old machine I'm perfectly happy with...

Considering [Moore's Law](http://en.wikipedia.org/wiki/Moore's_law)...yes :-P

---

### Post by Winnie the Pooh on 2006-12-05
Wow thanks endersshadow! Screen resolution worked like a charm :D But (oh not another) when I tried to get beryl, this appears....

```
........
Hit http://us.archive.ubuntu.com dapper-backports/universe Sources
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 25.5kB in 2s (12.1kB/s)
Reading package lists... Done
W: GPG error: http://www.getautomatix.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A947CF51609B551
W: You may want to run apt-get update to correct these problems
Winnie the Pooh@Winnie the Pooh-desktop:~$ sudo apt-get install beryl
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
         Depends: emerald but it is not going to be installed or
                  aquamarine but it is not installable or
                  heliodor but it is not installable or
                  compiz-gtk but it is not installable
         Depends: beryl-manager but it is not going to be installed
E: Broken packages
```

What do I do now?:confused: Thanks again in advance....

---

### Post by endersshadow on 2006-12-05
Run this command:

```
cat /etc/apt/sources.list
```

And post you output here.

---

### Post by Winnie the Pooh on 2006-12-05
```
Winnie the Pooh@Winnie the Pooh-desktop:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt dapper main

deb http://www.getautomatix.com/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#AUTOMATIX REPOS END

deb http://edevelop.org/ubuntu dapper e17
deb-src http://edevelop.org/ubuntu dapper e17

#Beryl
deb http://ubuntu.beryl-project.org/ edgy main
Winnie the Pooh@Winnie the Pooh-desktop:~$
```

:confused: :confused:

---

### Post by arnieboy on 2006-12-05
change
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
to
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main

---

### Post by Buck2348 on 2006-12-06
Does the above instruction for installing beryl apply to dapper as well as edgy?  I have an Intel 82865G graphics card and running dapper 6.06.  This is what I got when I tried to run beryl:

```
buck@Dmitri:~$ emerald &
[1] 6236
buck@Dmitri:~$ beryl &
[2] 6243
buck@Dmitri:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
```

I believe the XGL and AIGLX refer to drivers, but beyond that I'm lost.  Any help appreciated.

Buck

---

### Post by Winnie the Pooh on 2006-12-06
Hey Buck, that's just like what I got too....
```
Winnie the Pooh@Winnie the Pooh-desktop:~$ killall metacity
Winnie the Pooh@Winnie the Pooh-desktop:~$ emerald &
[1] 5268
Winnie the Pooh@Winnie the Pooh-desktop:~$ emerald: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

[1]+  Exit 1                  emerald
Winnie the Pooh@Winnie the Pooh-desktop:~$ beryl &
[1] 5277
Winnie the Pooh@Winnie the Pooh-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

[1]+  Exit 1                  beryl
Winnie the Pooh@Winnie the Pooh-desktop:~$

```
I am confused:confused: ... any help appreciated! Thanks!

---

### Post by endersshadow on 2006-12-06
Easy fix (woot):

```
sudo gedit /etc/X11/xorg.conf
```

Paste this code to the bottom:

```
Section "Extensions"
	Option	"Composite"	"Enable"
EndSection
```

Save and close.

Logout and then back in.  If beryl isn't working, simply open up a terminal and use:

```
beryl-manager
```

You won't have to bother with metacity :-D

---

### Post by d3v1ant_0n3 on 2006-12-07
If you're wanting to run Beryl on Ubuntu Dapper (6.06 LTS), you might want to read [ this ](http://forum.beryl-project.org/viewtopic.php?t=44) thread from beryl forums- apparently it has potential to break future upgradability.

---

### Post by endersshadow on 2006-12-07
The reason it will break is that Dapper needs to have AIGLX installed in order to run Beryl.  However, in Edgy, the version of X.org contains the AIGLX by default (and it is enabled).  Therefore, you simply need to install Beryl.  However, when you dist-upgrade from Dapper to Edgy, it will replace X.org but *not* remove AIGLX, thereby causing conflict and bringing Beryl to its knees.  If you are going to upgrade from Dapper to Edgy via a dist-upgrade (which I don't recommend because of all the problems associated), you *must* be aware of this and remove AIGLX prior to dist-upgrading.

:)

---

### Post by patagonik on 2006-12-07
Hy!!!

Little question: apparently i have the same Intel Graphic Card as you do, and the output when typing "sudo 915resolution -l" is exactly the same.I have been stacked using this 1024x768 resolution since the beginning of the "resistance" and i was wondering if it was really possible to change the resolution. In System-> Preferences-> Screen Resolution i can only choose the actual 1024x768 resolution. By doing "sudo 915resolution 43 1400 1050 32" will i really be able to change the resolution or my computer will explode?

I would like to know what to do in case of problems. Will i be able to change the resolution back?

I'll wait for an answer excited as a space monkey... unlimited possibilities in case of affirmative answer!!!   

pata

---

### Post by endersshadow on 2006-12-07
patagonik: Yes, yes it will really change your resolution.

Seriously, I'm not kidding :)

As for why your System -> Preferences -> Screen Resolution doesn't have it, it gets a bit low level, but suffice to say that X.org doesn't have the correct module for the chipset to support those resolutions natively.

Happy computing!

---

### Post by patagonik on 2006-12-07
Snif, snif... for once i believed and i have been terribly betrayed!!! :(  
In fact, even in the times where the windows didn't let me see the sun light i was unable to change the resolution. I guess it's inherent in my computer. I can diminish the resolution, never increase it. Good try anyway! 

... but still, i'll never believe again... snif, snif...  

VIVA LINUX!!!:D 

pata

---

### Post by endersshadow on 2006-12-07
pata: Post your /etc/X11/xorg.conf file.

---

### Post by Winnie the Pooh on 2006-12-07
Beryl is up and running... Thanks to everyone!! :-D

---

### Post by patagonik on 2006-12-08
Here it goes... too many times written 1024x768 right? 
Now it's when you said "Hmmm... Interesting"... give me good news man!



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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I wish you all a f***ing nice rainy day!

pata

---

### Post by endersshadow on 2006-12-08
Hmmm...interesting...

Try doing this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg
```

Paste this in over your existing one:

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Save and close that. Next:

```
sudo 915resolution 5a 1400 1050 32
```

Log out, then log back in.  If X goes crazy on you, press Ctrl+Alt+F1.  You'll be looking at a full screen terminal.  Log in, and then do:

```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

---

### Post by patagonik on 2006-12-09
Nothing happened... i've done exactly what you have told me. I really guess that is a ind of internal limitation of the whole computer, probably not from the graphic card. I have no idea though!

Anyway, i should thank you one more time for the effort!! That's what i like from all this ubuntu thing! 

My problem really was the window list...there is a screenshot. I don't wanna put panels everywhere and finally the available space for listing windows is rather limited. Never mind, i like it this way, and of course i got used long time ago. 

I would like to take advantage of this moment to wish you all a great weekend... finally the rain gave rise to a huge winter sun!

pata

---


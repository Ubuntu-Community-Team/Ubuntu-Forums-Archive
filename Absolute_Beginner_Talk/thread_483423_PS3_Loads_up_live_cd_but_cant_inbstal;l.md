---
title: "PS3 Loads up live cd but cant inbstal;l"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by lemonwonder on 2007-06-24
I load up the live cd but cant install

The install window comes up, I choose english but cant see the "next" button it is out of the view of my screen. I have downloaded 2.3gb of ubuntu stuff trying to get dis to work, plz  dnt tell me to download 677 mb of more stuff.

i went to preferences and reolutions, cant change it.


ubuntu-7.04-desktop-powerpc+ps3.iso

I can see the bottom bar, with the minimized windows etc, but the windows go UNDER that. How can i fix this?

---

### Post by w4ett on 2007-06-24
On the boot screen of the live cd is a selection for VGA.  Select this and see if you can change the default boot resolution to something bigger that will work for you.

---

### Post by lemonwonder on 2007-06-24
there is no boot screen. A thing comes up saying kboot boot loader the default option is live if you are unsure just press enter. I did live coz i wanted live cd

---

### Post by w4ett on 2007-06-24
the boot screen is on the Ubuntu (Gnome)  live CD....Sorry didn't know you were using KUbuntu...not sure about that one.

---

### Post by lemonwonder on 2007-06-24
NO! I using Ubuntu Fiesty Fawn. 7.04. PS3 edition

---

### Post by w4ett on 2007-06-24
Try right clicking on both the upper and lower bars and select autohide for each of them and then maximize the widow......the "next" button is the one on the far right at the bottom of the window.

---

### Post by lemonwonder on 2007-06-24
Thnx for that ill try now. Also, PS3 partitions the disk automatically thru XMB, do i select "Use whole drive for linux" or "split drive" although its alredy been split

---

### Post by lemonwonder on 2007-06-24
I tried it. I cant see the button. It is still out of reach. Even with both bars hidden!

---

### Post by w4ett on 2007-06-24
Just for giggles and grins....click on System>Preferences>Screen Resolution....Try Clicking and hold the button down to scroll and see if you can get any other resolution...

---

### Post by lemonwonder on 2007-06-24
Tried dat. It only has 1 resoluton and 25mhz refresh rate

---

### Post by nutz on 2007-06-24
[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

---

### Post by lemonwonder on 2007-06-24
that doesnt help very much...

---

### Post by w4ett on 2007-06-24
Let's see what's in your xorg.conf file. in the terminal type this:

sudo gedit /etc/X11/xorg.conf

and post the contents of the file....Maybe we can make some manual adjustments to your screen resolutions to get you through installation.

---

### Post by lemonwonder on 2007-06-24
k lemi run to ps3, do I have to write it ALL down on paper? Also, do you have msn or windows messenger

---

### Post by w4ett on 2007-06-24
the live cd should be able to connect to the internet if it's connected via ethernet.......My If you have AOL my username is w4ett or also on irc if you prefer.  

the section of the xorg.conf section we are looking for will look something like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9200SE"
	Monitor		"Dell E773c"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by lemonwonder on 2007-06-24
In the terminal alot of stuff came up saying device not found etc, then the file opened, Line 1 Col 1 BLANK... no more lines

---

### Post by w4ett on 2007-06-24
Sorry I made a typo...I just corrected it....

sudo gedit /etc/X11/xorg.conf

try it again. please

---

### Post by lemonwonder on 2007-06-24
Managed to get it up, opening firefox on ps3... takin a while but ill post soon

---

### Post by nutz on 2007-06-24
> **lemonwonder said:**
> that doesnt help very much...

From that I got...

Users of standard definition TVs are recommended to use the alternate installer discs to install Ubuntu as you will have a very low resolution to go through the installer wizard of the desktop installer discs. Have you tried the alternate installer?

---

### Post by w4ett on 2007-06-24
cool.....

---

### Post by lemonwonder on 2007-06-24
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Option		"XkbOptions"	"lv3:lwin_switch"
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
	Identifier	"Generic Video Card"
	Driver		"fbdev"
	Option		"ShadowFB"		"false"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	DefaultFbBpp 32
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection





And i wana try fix it without downloading anither 677mb and putting intrnet speed down to 50kbps (this line is for nutz)

---

### Post by w4ett on 2007-06-24
Ok....next question...what make/model monitor are you using?  We need to look up the resolution and refresh rates for it, so we can modify the file.

---

### Post by lemonwonder on 2007-06-24
Im using a SDTV (remember, its PS3) ill measure:

40cm across

30cm down.

Thats the screen, excluding the casing :)

Its a JVC

---

### Post by nutz on 2007-06-24
Users of standard definition TVs are recommended to use the alternate installer discs to install Ubuntu as you will have a very low resolution to go through the installer wizard of the desktop installer discs.

---

### Post by w4ett on 2007-06-24
> **lemonwonder said:**
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Option		"XkbOptions"	"lv3:lwin_switch"
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
	Identifier	"Generic Video Card"
	Driver		"fbdev"
	Option		"ShadowFB"		"false"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	DefaultFbBpp 32
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection





And i wana try fix it without downloading anither 677mb and putting intrnet speed down to 50kbps (this line is for nutz)

1024x768  should give you the required resolution that you are looking for.....what resolution is showing up in System>Preferences>Screen Resolution?

---

### Post by lemonwonder on 2007-06-24
kk lemi go chek.... and it wont change it thru there brb

---

### Post by w4ett on 2007-06-24
1024x768 should give you enough "real estate" on an sdtv to be able to install successfully.  If we can't get your screen resolution to change on the live cd, you will need to consider d/l'ing the alternate install cd.  I know it's a pain in the butt, but sometimes you need to drop back and punt....LOL  8)

---

### Post by nutz on 2007-06-24
> **w4ett said:**
> you will need to consider d/l'ing the alternate install cd.  I know it's a pain in the butt, but sometimes you need to drop back and punt....LOL  8)

If he had started the download when his troubles began it would probably be done by now.

---

### Post by w4ett on 2007-06-24
> **nutz said:**
> If he had started the download when his troubles began it would probably be done by now.

True enough nutz, but a positive learning curve is a good thing too.

---

### Post by Bohlio on 2007-06-24
Just to pop in and add my 2 cents... Is your TV zoomed at all?? I know some tvs have settings to adjust with like full, zoom, centered, and so on.... I hope you get it worked out :-P

---

### Post by lemonwonder on 2007-06-24
576X460 is the res..and 25mhz. Cant change

---

### Post by lemonwonder on 2007-06-24
Ooo alot of replies. And no, the download take 9 hours on top of the line NZ connection....

---

### Post by w4ett on 2007-06-24
this line:

Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"

Tells me that you should have those three resolutions available from the live cd that is running now.  I have no idea why you are unable to reset your screen resolution...It SHOULD work.  One work around is that if you have an DVI to analog adapter and connect to your computer monitor....as far as I know this will give you 720p and WILL be fully compatable.

---

### Post by lemonwonder on 2007-06-24
Hmm.... i have a few cd's which may actually have alternate on em... trying now

---

### Post by w4ett on 2007-06-24
> **lemonwonder said:**
> Hmm.... i have a few cd's which may actually have alternate on em... trying now

Good luck...we'll be waiting....I'll be here for about another hour or so....it's it's 0415 UTC here.... :)

---

### Post by lemonwonder on 2007-06-24
the 2 i have didnt work.

Can u write a detailed guide on installing with alternate cd? People told me its diff and had bugs. So simple a fly could do it... eg.

Turn on PS3

Put CD in and go to install other OS

Move the mouse right until its ontop of a button saying next

Etc etc>... could ya?

---

### Post by w4ett on 2007-06-24
here's the best how-to that I know of......let us know how you make out with it.

[http://ubuntuforums.org/showthread.php?t=316047](http://ubuntuforums.org/showthread.php?t=316047)

---

### Post by lemonwonder on 2007-06-24
I  am sorry but can you translate that to dummy for me?

Its got fedoras and boots and straps omg i dont understand.

i just wana install ubuntu onto my ps3.... thats all..

---

### Post by w4ett on 2007-06-24
The very last posting in the thread says:

QUOTE:

From  HOBBITCY
 Re: HOWTO: PlayStation 3 - Installing Ubuntu on the PS3
hi guys iv just skipped most of the howtos well i read a bit and i got ubuntu on my ps3
what i did was get the PPC version my understating is this is the only version that will work
im almost sure its a 32bit version
and its also a custom live cd coz the ordinary version wouldnt install properly
just poped the disk in pressed install and went through the 7 steps restarted and i was in ubuntu..

UNQUOTE

Since the release of Feisty Fawn 7.04, you do not need any additions to install Ubuntu...it should install ok as it is fron the Live CD...In your case however, with the resolution problem I recommend that you use the Alternate Install CD...this will allow you to install in a text based environment, and give you better control on your install options.

Considering you cannot attach your PS3 to a widescreen or HDTV monitor, this is probably the method you should consider.  Long D/L times can be shortened by use of a library connection or a cybercafe Maybe?  Apart from that I've run out of options.

---

### Post by lemonwonder on 2007-06-24
Hmm, so if i go upstairs and connect to parents HDTV and install, can i change resolution to work on my SDTV. And what res should i make it?

---

### Post by w4ett on 2007-06-25
> **lemonwonder said:**
> Hmm, so if i go upstairs and connect to parents HDTV and install, can i change resolution to work on my SDTV. And what res should i make it?

Yes it should be possible by modifying the xorg.conf file when it's installed.

---

### Post by lemonwonder on 2007-06-25
For a tv 40cm accross and 30cm down (just the screen display part) what and how do i edit??

---

### Post by w4ett on 2007-06-25
> **lemonwonder said:**
> For a tv 40cm accross and 30cm down (just the screen display part) what and how do i edit??

What we'll do is select the highest resolution...i.e: 1024x768 as your default resolution from the login screen after you have a working installation.

---

### Post by lemonwonder on 2007-06-25
I took it upstairs. (used colour plugs coz dont have HDMI cable) and I eventually found out I can just press enter (i couldnt see the next button up their ether) its at 15%, has been for about 5 mins.... disc i can hear spinning so...

---


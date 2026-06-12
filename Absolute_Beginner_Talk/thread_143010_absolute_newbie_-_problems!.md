---
title: "absolute newbie - problems!"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by vixenk on 2006-03-11
I just installed Ubuntu and have came across two problems. First of all, in the screen resolution menu I'm unable to select the screen resolution I want *1280x1024* even though my monitor is more than able to handle that resolution. Any workarounds for this? Second, I'm unable to access my backup hdd. I went to the Disks Manager and it shows up as a hdd but access path says none and status says inaccessible. Does this mean that I'll have to trash 200 gigs of data in order to use Ubuntu just because it's Windows NTFS formatted, or is there something I can do to gain access to it again?

---

### Post by bluevoodoo1 on 2006-03-11
1. ```
sudo dpkg-reconfigure xserver-xorg
```
 When you get to the screen resolution page, hit the space bar at the 1280x1024 option.

2. [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

---

### Post by vixenk on 2006-03-11
Ok... lol, where is the command prompt in this os?

---

### Post by bluevoodoo1 on 2006-03-11
ohh! whoops! :) applications > accessories > terminal

---

### Post by vixenk on 2006-03-11
Nevermind, I found it.

---

### Post by vixenk on 2006-03-11
ROFL... I'm having issues getting to the part about the screen resolution I have no idea how to answer the kernel framebuffer device interface question. :P

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=vixenk]ROFL... I'm having issues getting to the part about the screen resolution I have no idea how to answer the kernel framebuffer device interface question. :P[/QUOTE]

Hmmm... I believe the default is "no." Just leave whatever is suggested for the questions that you are unsure of. :)

---

### Post by vixenk on 2006-03-11
I just went ahead and pressed enter on everything hoping it was already on its default selections. However, even though I selected 1280x1024 from the screen resolution menu, it still won't let me use that resolution.

---

### Post by vixenk on 2006-03-11
erm, rephrase - I tried my best to go with the suggestions, I didn't just press enter on everything, lol.

---

### Post by vixenk on 2006-03-11
Oh, one more thing *sorry to be such a pain in the butt :P*... that link you sent me only gives instructions on how to enable reading the hdd, but says nothing about writing to it *on a NTFS format, that is*. Does that mean it's not possible or just not covered in the material?

---

### Post by bluevoodoo1 on 2006-03-11
Probably have to restart X. Try Ctrl+alt+backspace. That should put you back to the gdm. If you end up at a command line you have to type

sudo /etc/init.d/gdm restart

If that doesn't do it. Paste the contents of /etc/X11.xorg.conf 

gedit /etc/X11.xorg.conf and copy/paste here.

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=vixenk]says nothing about writing to it *on a NTFS format, that is*. Does that mean it's not possible or just not covered in the material?[/QUOTE]

Ohh... Yeah, you can't write to NTFS. :/


EDIT: Rearding resolution,... After you have restarted X, you may have to still change your resolution from the menu system > preferences > screen resolution.

---

### Post by vixenk on 2006-03-11
Ok, restarting did not help. Still can't get a 1280x1040 resolution in the options. And it's the screen resolution menu under preferences that I'm talking about. :)

Also, whenever I try the commands for mounting NTFS, it asks for my password, but literally won't let me type my password in. I thought maybe it just didn't show anything when you type in your password but after going ahead and typing it and pressing enter it tells me I have the wrong password. Arghhhh...

NOW I'm getting frustrated. First of all, I don't have the space to move everything on my secondary hdd and reformat it just so I can make changes to the data on it. Second, at the very least I have to access the data on it because well, it's my backup hdd. It has everything. I know Ubuntu is supposed to have a learning curve but sheeeeesh!

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=vixenk]Ok, restarting did not help. Still can't get a 1280x1040 resolution in the options. And it's the screen resolution menu under preferences that I'm talking about. :)

Also, whenever I try the commands for mounting NTFS, it asks for my password, but literally won't let me type my password in. I thought maybe it just didn't show anything when you type in your password but after going ahead and typing it and pressing enter it tells me I have the wrong password. Arghhhh...
[/QUOTE]

Can you paste here the contents of /etc/X11/xorg.conf so we can see what exactly is going on with your resolution. gedit /etc/X11/xorg.conf

That's odd the password isn't working. You were able to put your password in for sudo dpkg-reconfigure xserver-xorg without any problems right? Should be your same password.

---

### Post by vixenk on 2006-03-11
Yup, I was able to do that, but it just won't let me do this one. And I'm using the same password. Nothing shows up on the screen whenever I start typing it, though, like it doesn't even realize I'm using the keyboard.

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

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600 M10 (RV350 NQ)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
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
	Device		"ATI Technologies, Inc. Radeon Mobility 9600 M10 (RV350 NQ)"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by vixenk on 2006-03-11
Wait a minute...

Can't I just edit this file I just pasted?

---

### Post by bluevoodoo1 on 2006-03-11
Before you mess with the xorg.conf file you should make a backup...

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

ok... now open the xorg.conf with...

```
sudo gedit /etc/X11/xorg.conf
```

try adding "1280x1024" to your monitor modes area. 

```

Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"

```

Save it, then restart X. Log back in... and see!

The password thing seems normal. It is normal not to see anything when typing your password. This stumped me when I first started using Ubuntu.

---

### Post by vixenk on 2006-03-11
Ok, I tried again, this time my password worked, but on the second command that involved mounting the hdd, I got this:

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by bluevoodoo1 on 2006-03-11
What were the exact commands you wrote? Paste them in here.

---

### Post by vixenk on 2006-03-11
Ok, just got done restarting, still no luck on the screen resolution options. :S

The commands for mounting the hdd I used were:

1. sudo mkdir /media/windows *I pressed enter here*
2. sudo mount /dev/sda /media/windows/ -t ntfs -o nls=utf8,umask=0222 *pressed enter again*

---

### Post by bluevoodoo1 on 2006-03-11
Well. I'm stumped on the resolution. The only other thing I'm thinking is that it's the horizonal sync /vertical refresh rates. Have you used this monitor on another operating system at 1280x1024? What model is it?

hmm for the mounting. Can you paste here the output of cat /etc/fstab ?


Edit: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) talks about chaning your monitor's refresh rates. I've never done it, so I probably wouldn't be too much help.

---

### Post by vixenk on 2006-03-11
Ok, I just noticed I was missing the 1 after sda, so I added that. Still got the same error, though. :S

---

### Post by bluevoodoo1 on 2006-03-11
Please paste in the contents of the terminal window. (don't just retype it here, paste it all in here) This way, specifics can be seen easier.

---

### Post by vixenk on 2006-03-11
Yes, I've used this monitor on another OS *WinXP Home & Pro* at that resolution, right up until I installed Ubuntu today. It's a Compaq 7550 17 inch flatscreen CRT, and can handle that resolution up to like 75 hz. Right now I'm running at 60.  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

In the Disks Manager it shows my backup HDD's location as being /dev/sda1. *dunno if that helps any*

---

### Post by vixenk on 2006-03-11
vixenk@sable:~$ sudo mount /dev/sda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000s
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=vixenk]vixenk@sable:~$ sudo mount /dev/sda1 /media/windows/ -t **vfat** -o iocharset=utf8,umask=000s
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/QUOTE]

Now we're getting somewhere! You said that HDD is NTFS right??

then it should be...

```
sudo mount /dev/sda1 /media/windows/ -t **ntfs** -o nls=utf8,umask=0222
```

Seems like you copied/pasted from the FAT partition guide instead of the NTFS guide.

---

### Post by vixenk on 2006-03-11
Oops, lol. I thought I was copying from the NTFS guide. :S

And it worked! Thanks. :) Now I've just got to get this pesky resolution thing settled plus figure out how to get my 4th and 5th mouse buttons to work, lol.

---

### Post by bluevoodoo1 on 2006-03-11
ok... I was thinking it might be a driver issue. This is a great guide...
[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)


[http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=219439&targetPage=http%3A%2F%2Fh20000.www2.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc00385928%2Fc00385928.pdf](http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=219439&targetPage=http%3A%2F%2Fh20000.www2.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc00385928%2Fc00385928.pdf)

Should be a link to your monitor's manual. I'm not sure which 7500 you have. But it has the horizontal / vertical rates there. You might want to experiment with if you want to take that route. 

I found this link for your mouse....
[http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse](http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse)

---

### Post by xmastree on 2006-03-11
Edit: never mind, I see the refresh rates are already in your xorg.conf :-# 

Too early in the morning, caffeine hadn't kicked in yet... :rolleyes:

---

### Post by vixenk on 2006-03-11
bluevoodoo1, I tried the mouse thing, and ended up with some wierd blue screen at startup about the x server. And of course, with that on my screen, I couldn't come back to the forums for help, lol.

That's the point where I said screw it and decided it was time to try out the copy of Mandrake I've had but never tried out *3 cds is a bit intimidating, but the installation time ended up being only 7 minutes, lol*. It's turning out to be much nicer/easier to use + I haven't had a single driver issue despite it being an outdated copy. So I'm probably going to stick to it for a while and leave Ubuntu for in the future when I get more comfortable and familiar with Linux.

Thanks for your help, everyone. :) It just got to be too much, though.

---

### Post by asusa83 on 2006-03-12
Hello, 

So, I'm one of those who 'just got Ubuntu in the mail today!' and decided to have at it.  The install went, it seems, successfully although I botched the screen resolution selection...after reading this topic.

I read this:
[QUOTE=bluevoodoo1]
try adding "1280x1024" to your monitor modes area. 

```

Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"

```

Save it, then restart X. Log back in... and see!
[/QUOTE]

tried it, and found that between the boot screen and log-in screen my monitor behaves like it has a mind of its own.  A configuration window (belonging to the monitor itself) bounces around telling me that I'm not using the correct resolution and that it recommends 1280x1024.  This happens to be the resolution I'm trying to recommend it uses also ;) 

The problem is that I'm unable to see anything or log into Ubuntu to change anything :(  Several restarts have been done by now and I don't know what to do...which is why I post here.

Your help will be appreciated.  The main question, I suppose, is how do I change anything in Ubuntu if I can't login :-k  ?

Thanks!

---

### Post by shuttleworthwannabe on 2006-03-12
Hey,

Tell us more about your hardware: make, graphics card type (i810, ATI, nVidea, etc). Resolutions possible? and what drivers have you installed/not installed?

This has happened to me before, and your problems sounds fixable. Have you tried reconfiguring xserver, see this link if it applies to you: [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by asusa83 on 2006-03-12
Shuttleworth, 

Is your above reply directed at myself?

:-k

---

### Post by asusa83 on 2006-03-12
In any case, here's my system info:

Samsung Syncmaster 930B Monitor:
[http://www.samsung.com/Products/Monitor/LCD_Digital/BI19BSSB.asp]("http://www.samsung.com/Products/Monitor/LCD_Digital/BI19BSSB.asp")

Intel 82865G Graphics Controller:
[http://www.intel.com/support/graphics/intel865g/]("http://www.intel.com/support/graphics/intel865g/")

The computer is an Acer running WinXP Pro SP2 and, in case no one feels like visiting the Samsung link, it's capable of doing 1200x1024.

For the record, I will admit that during the second phase of installation (after removing the boot disc & restarting) it asked me to choose the resolutions I wanted to be available.  I tried to select one and the installation process moved on to the next screen without me...

I haven't gotten around to installing any drivers yet ... it's more of my style to break things first :-#   

Again, your help will be super-appreciated:)

---

### Post by shuttleworthwannabe on 2006-03-12
Ok. See these instructions: [https://wiki.ubuntu.com/i915Driver](https://wiki.ubuntu.com/i915Driver)

You are in a black screen right? login, and 
$ sudo dpkg-reconfigure xserver-xorg

Select default settings, until you get to display section: Choose VESA is the diplay type. and I would just choose the resolutions that your display can show. I like to choose 1024x768 to be safe. Complete the configuration by choosing the default settings, and reboot. 

Now this will aloow you get into the GUI mode at least. Login and see if you are in GUI. Go to synaptic and install 915resolution patch.

Then follow these instructions: [http://users.skynet.be/thomasvst/linux-on-laptop/#wide](http://users.skynet.be/thomasvst/linux-on-laptop/#wide)

the instructions are for a laptop, but should work. 

Please post back what your experience has been.

regards,
S

---


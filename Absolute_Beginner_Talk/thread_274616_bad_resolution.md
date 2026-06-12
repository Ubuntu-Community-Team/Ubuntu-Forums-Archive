---
title: "bad resolution"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by deadwalkin on 2006-10-10
OK i have been useing fedora 

and i have seen this looks nice shame i cant see a good res i can use it as in VGA but if i change res to anything else it will not give me a display.

can any one help me.

and this is from boot on the disc i want the program to be in stalled on a samsung V25

please help..
all the best

---

### Post by Jamhos on 2006-10-10
I had resolution problems booting from the Live CD on my desktop PC (but not on my laptop, strangely enough), but it was all fine once I actually installed Ubuntu onto the hard drive.

---

### Post by jorn on 2006-10-10
Just to clearify:
You installed Ubuntu and can't change to prefered resolution?
Are you posting from install-cd?

---

### Post by deadwalkin on 2006-10-10
i Have used the ISO to install it from the live cd but when i have installed ubuntu the res stays the same and it will not let me change it in the resolution menu it stays at 600 something and 60hz.
i no you can select what res you want when you first put the disk in but then when it gets into the main screen i get the sound but no desk top

I.E trying to install the full program on hard drive

---

### Post by ske1fr on 2006-10-10
> **deadwalkin said:**
> i Have used the ISO to install it from the live cd but when i have installed ubuntu the res stays the same and it will not let me change it in the resolution menu it stays at 600 something and 60hz.
i no you can select what res you want when you first put the disk in but then when it gets into the main screen i get the sound but no desk top

I.E trying to install the full program on hard drive

Please tell us what graphics card (or chipset) your computer contains, and whether or not the computer is a laptop.  This may help those with experience decide how to help you!  I don't count myself in that category...[edit] Come to think of it, I have got my laptop working, and I've got my NVidia 6200 Turbocache card working , so perhaps I should rethink that.

---

### Post by jorn on 2006-10-10
All the different resolutions(and everything that has to do with your monitor) are listed in /etc/X11/xorg.conf. By adding more res. you might be able to solve your issue.
Would you post your /etc/X11/xorg.conf

---

### Post by Comendante on 2006-10-10
If you want change your resolution, edit file /etc/X11/xorg.conf.
And in section "Screen" - Serach "Modes" and write your resolution, near that.

---

### Post by deadwalkin on 2006-10-10
Hardware
Samsung V25 Laptop 
Intel Pentium 4 2.66Ghz (SSE2 max) 
Intel 845GV Chipset 
512MB SDR-SDRAM Shared 
40GB HDD 
Intel 845GV Graphics 8MB Shared 
AC97 Audio Codec and LAN 

i have just pluged the laptop into a tft monitor and i have a destop remove the rgb cable and restart
have sound but no desktop
put windows back on it works fine reinstall ubuntu and it still will not show a desk top in res 1024x768 refresh rate 85hz

the thing is it will show me desktop in normal vga but i dont no how to change it to the higher res as it will not give you this option in the menu it will stay at something like 600

---

### Post by Perfect Storm on 2006-10-10
Try with
```
sudo dpkg-reconfigure -phigh xserver-xorg

```

restart X ctrl+alt+backspace

---

### Post by deadwalkin on 2006-10-10
i have done these but still the same. :-(
well sort of i have rebooted the pc have sound but no desktop again lol
also i have restarted the pc with tft screen and i have my desktop back on the laptop at the right res but if i take it out the lap top goes to no desktop when rebooted

---

### Post by deadwalkin on 2006-10-10
or do i need to get a driver for this issue if so where do i get it from please

---

### Post by ske1fr on 2006-10-10
You probably have the relevant driver already, but we'll only know what's happening if you post the contents of the file  /etc/X11/xorg.conf as jorn said.  Sometimes a specific display device needs special options adding to this xorg.conf file so as to activate the full features.

Your laptop should be using the i810 driver, if I understand it correctly.  There's a great deal of information at [the Xorg website](http://xorg.freedesktop.org/archive/X11R7.0/doc/html/i810.4.html) that may be relevant, particularly about checking the X.org logfile for error messages.

---

### Post by yasoumalaka on 2006-10-10
I tried this and it gave more resolutions, but not the one I picked. I have a 6600gt connected to a samsung syncmaster 204b. What could be the cause?

---

### Post by bulldog on 2006-10-10
Take a look at this link,maybe it's helpfull.

[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

---

### Post by yasoumalaka on 2006-10-10
Ok I have the nvidia driver installed. I've put in all the info for my monitor and I've enterd the resolution.All of this appears in the xorg.conf file, but I'm still not at the right resolution. This si wierd because in suse I had the right resolution. Any ideas?

---

### Post by CatKiller on 2006-10-10
Why would you install the NVidia driver? From what you've said, you don't have an NVidia card. As ske1fr said, you'll probably want the i810 driver, but we can't tell what you're using, or what the problem is, unless you post the contents of your /etc/X11/xorg.conf file. That is where drivers, resolutions and refresh rates are set.

---

### Post by yasoumalaka on 2006-10-10
You're are refering to two different people, I was the second newb to post about res issues. I know I have a nvidia card and I just wanted to tell you what I had to done to no avail. Here is my xorg.conf

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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nv"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
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

As you can see 1600x1200 should be my only option in resolution options, but I have every res except 1600x1200 to choose from.

I have a samsung syncmaster 204b

Thanks!

---

### Post by CatKiller on 2006-10-10
Sorry. I got confused :) Some quick suggestions for you, then. You could run ```
sudo nvidia-glx-config enable
```or change the **"nv"** line to **"nvidia"**.

Or you could change> Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection to > Section "Monitor"
    Identifier "Samsung SyncMaster 204B"
        Option "DPMS"
        HorizSync 30-81
        VertRefresh 56-75
EndSection

---

### Post by deadwalkin on 2006-10-11
thanks guys i have found out what was wrong i did not have this in the file


HorizSync 28-80
VertRefresh 43-60

thanks for the help

---

### Post by yasoumalaka on 2006-10-11
Sorry for some reason my xorg.conf didn't save the entries I added. I tried all your suggestions and none of  them worked so far. The sudo nvidia-glx-config enable gave me command not found. Any other ideas? This is frustrating. I  have had this working  in many other distros. I love ubuntu and my damn screen isn't at the right res.](*,)

---

### Post by jorn on 2006-10-11
Did you open the editor with:
> sudo gedit /etc/X11/xorg.conf
in order to save the file?

---

### Post by yasoumalaka on 2006-10-11
Yep. The button can't be pushed if you don't do so.

---

### Post by Perfect Storm on 2006-10-11
See if you can safe the file with nano instead gedit.

---

### Post by CatKiller on 2006-10-11
> **yasoumalaka said:**
> The sudo nvidia-glx-config enable gave me command not found.

That suggests that you don't have the NVidia driver installed. Some people have a moral objection to using it, since it is closed-source. If you are one of these, then use the nv driver. I understand that it's pretty decent, although I don't believe that it has 3D stuff.

If you would like to install the NVidia proprietary driver, the commands to do so are ```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```If you've modified your /etc/X11/xorg.conf file, you may still need to change the "nv" to "nvidia".

---

### Post by yasoumalaka on 2006-10-12
Ok catkiller I tried what you said and it worked until I restarted xserver and I couldn't get into graphical mode. I fixed it and went back and had to reenter my monitor info and then when I restarted I wasn't able to get into graphical mode. Whats up with getting the nvidia drivers off their website? Thats where I got thtem initially. This is really frustrating. WTH is up with my ubuntu?

I might just do a reinstall. I don't want to get off topic but I get this message when I try to use the software managaer 

[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)

What is this? I thought a server was down but its been like this for  days now.

---

### Post by CatKiller on 2006-10-12
So you're using 64-bit Ubuntu? Crikey. I understand that that is significantly less user-friendly than the 32-bit version. If you're planning a re-install anyway, it might be worth going for the 32-bit version for a while until you're more used to it.

I don't know how to configure the drivers from the NVidia site - I've never used them. Packages from the repositories are much better supported by Ubuntu.

---

### Post by yasoumalaka on 2006-10-12
I didn't realize there was a difference. I have 32bit on my laptop it works fine. Will 32bit be slower? I have an OCed opteron I just thought 64bit was more fitting.

---

### Post by Perfect Storm on 2006-10-12
You will not feel the diffrence (well it's so little anyway). Most applications and games doesn't take advantage of 64 bit yet so it's a bit tit for tat.
32bit is more user friendly (in newbie term).

---

### Post by yasoumalaka on 2006-10-12
Cool I am installing it now. I really want to try everything ubuntu has to offer with out restrictions. So 32bit sounds better at the moment. Although I would learn some fromthe challenge of using 64bit ubuntu. Thanks.

Its a no go. the 32bit freezes at the partitioner. I still want it.any suggestions. any morepost on this and aI'll make a new thread.

I have an opteron
dfi mobo

---

### Post by yasoumalaka on 2006-10-12
Ok catkiller your method worked after the reinstall. It must have been the nvidia driver off their site that screwed things up. Thanks, Now I have my resolution at 1600x1200. I just need to get that one package to dl now. Thanks everybody for the help.

---


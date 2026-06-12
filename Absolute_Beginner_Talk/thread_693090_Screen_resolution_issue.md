---
title: "Screen resolution issue"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Miller12 on 2008-02-10
I am new to Ubuntu (and Linux) and I have installed 7.10 on a Dell Inspiron 5150 laptop. I have got the nvidia card and wireless working but I am having trouble with the laptop screen resolution. It has S-video out so is the max res only for that and the monitor is holding me back? The way I read is I should be able to get 1400x1050 although I only want 1280x1084.

This is what the manual says

```

Display
Type (active-matrix TFT)            XGA or SXGA+ (Inspiron 5100)
                                    SXGA+ or UltraSharpTM UXGA
                                    (Inspiron 5150)
Dimensions:                         14.1 inch (Inspiron 5100 only) or 15 inch
  Height:
     14.1 inch (Inspiron 5100 only) 215.8 mm (8.5 inches)
     15 inch                        229.7 mm (9 inches)
  Width:
      14.1 inch (Inspiron 5100 only) 287.1 mm (11.3 inches)
      15 inch                        305.7 mm (12 inches)
  Diagonal:
      14.1 inch (Inspiron 5100 only) 359.16 mm (14.1 inches)
      15 inch                        380.1 mm (15.0 inches)
Maximum resolutions                  1024 x 768 at 16.8 million colors (XGA);
                                     1400 x 1050 at 16.8 million colors (SXGA+)
                                     1600 x 1200 at 16.8 million colors
                                     (UltraSharp UXGA)
Response time (typical)              20-ms rise (maximum),
                                     30-ms fall (maximum) (XGA and SXGA+)
                                     9-ms rise (maximum),
                                     16-ms fall (maximum) (UltraSharp UXGA)
Refresh rate                         60 Hz

```

but all I am getting is a generic monitor and 1024x768 at 50Hz

Here is some info. Any help is greatly appreciated.


/etc/X11/xorg.conf
```

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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34M [GeForce FX Go5200 64M]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34M [GeForce FX Go5200 64M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

sudo xrandr
```

Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0  
   800x512        52.0  
   720x450        53.0  
   640x512        54.0  
   640x480        55.0     56.0  
   640x400        57.0  
   640x384        58.0  
   512x384        59.0  
   400x300        60.0  
   320x240        61.0 
```

sudo ddcprobe -?
```
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV34 Board - p135nz Chip Rev
memory: 65536kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
edid: 
edidfail

```

sudo xresprobe any
```
id: 
res: 
freq: 
disptype: lcd/lvds

```

---

### Post by benfindlay on 2008-02-10
Launch a terminal and type ```
sudo dpkg-reconfigure xserver-xorg
```
Put your password in and follow the onscreen prompts

When you get asked for a choice of simple, medium and advanced, chyoose medium and you can select the resolutions you want by pressing space bar to put an * in the selection box. Then press enter when done

Hope this helps!

---

### Post by theRightNee on 2008-02-10
go to system>administration>screens and graphics
then choose which set up fits you the best and it should work out ok....

---

### Post by Rocket2DMn on 2008-02-10
Sounds like you need to reconfigure X so it offers you the correct screen resolutions ( xorg only shows 1024x768 ).  This problem is fairly common, so here is a guide for you - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by JoshuaRL on 2008-02-10
Should be as easy as going into xorg.conf and adding whatever desired resolution into Section "Screen" Subsection "Display" Modes.  Just make sure you backup your xorg.conf and only add a resolution the screen for sure supports.  Then save and restart Xorg.

---

### Post by Miller12 on 2008-02-10
Thanks I will give it a try but I have a few questions first.

A. Do I need to be concerned that it currently says "Generic Monitor" or was that just a failure of the autodetect?

B. To be safe do I go with the SXGA+ -> 1400 x 1050 at 16.8 million colors (SXGA+)? In the options when going through the reconfig is that the 16 option?

---

### Post by Rocket2DMn on 2008-02-10
Generic Monitor is usually OK, you can set it later from System->Administration->Screen and Graphics if you want.
For your second question, if you're talking about Depth, 24 will probably work, that's what I use on my Dell 600m @ 1400x1050.

---

### Post by Miller12 on 2008-02-10
I have followed the tutorial and tried to use a "Dell 1400x1050 LCD laptop only" in the "screens and graphics". It's weird maybe 1024x768 is my max

After reconfiguring X-server I am still only getting a 1024x768 option is "screens and graphics" or "screen resolution"

My xorg.conf file does say that the screen selections I made during reconfiguring Xserver are there:
```

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
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"NVIDIA GEFORCE FX GO5200"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GEFORCE FX GO5200"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050" "1280x1024" "1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by Rocket2DMn on 2008-02-10
Have you tried the open source "nv" driver instead of the nvidia proprietary one?
I think that 1024x768 might be the max on s-video out though (in fact I'm almost sure.  I know my s-video never did better than that).  Standard television is like 800x600 (not HD tv).

---

### Post by Miller12 on 2008-02-10
Rocket2DMn,

Thanks a lot for your help. I am not worried about the Svideo out res. since I am not planning on using it.

The driver I am using is from the restricted drivers manager and being a noob I am not sure on how to get the other one.

Just search the repositories for "nv'?

---

### Post by JoshuaRL on 2008-02-10
I think there's something you can add along the lines of 'DefaultResolution "1400x1050"', but I'm not sure how it goes exactly.  Try looking through this while I search:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

EDIT:  Okay, I found this for nVidia cards that allows you to edit the settings:

```
sudo apt-get install nvidia-settings
```

---

### Post by Rocket2DMn on 2008-02-10
> **Miller12 said:**
> Rocket2DMn,

Thanks a lot for your help. I am not worried about the Svideo out res. since I am not planning on using it.

The driver I am using is from the restricted drivers manager and being a noob I am not sure on how to get the other one.

Just search the repositories for "nv'?

the nv driver is available when you reconfigure X.  You could edit xorg.conf manually and change "nvidia" to "nv" and restart X with CTRL+ALT+BACKSPACE
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Miller12 on 2008-02-10
Well I not sure where to go from here:

I tried changing nvidia to nv - no higher resolution options and no desktop effects

Went back to nvidia and tried adding a modline with no success the /var/log/Xorg.0.log says that it didin't like the changes and switched to default with 1024x768@60 as the max.

gksudo nvidia-settings brought up the nvidia GUI and it states that the screen native resoltuion is 1024x768

In "Screen and Graphics" I changed the screen model to LCD Panel 1280x1024 and was able to get the resolution to run at 1280x1024 but it was to big for my display so I had to "push" on the side around the screen to see things that had 'fallen off the edges'. Could this be a function of the driver/video card setup or is the screen really 1024x768 even though the online manual says different? I really wish I could tell what display it is and then I could find the native resolution online.

---

### Post by Rocket2DMn on 2008-02-11
You could look at installing the nvidia drivers from nvidia's website.  You might have more luck with that - [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Miller12 on 2008-02-11
> **Rocket2DMn said:**
> You could look at installing the nvidia drivers from nvidia's website.  You might have more luck with that - [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Rocket2DMn (and others),

Again thank you for your help. At this point I am going to live with 1024x768, it's not horrible. Getting the drivers form the website is more complex than my skills allow since the following is needed:
* development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed
* the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

and more

Once I have learned a little more, or the next Ubuntu release comes along, I will try again.

Thank you,
Ryan

---

### Post by johnjreeve on 2008-05-14
I am having the same issues described in this thread, except with the Radeon Mobility 7500 video card. I looked in the tech docs that came with the Inspiron 5100 laptop and found this:

Maximum resolutions                  1024 x 768 at 16.8 million colors (XGA);
                                     1400 x 1050 at 16.8 million colors (SXGA+)
                                     1600 x 1200 at 16.8 million colors

First, how do I find out if the screen is XGA or SXGA?

Second, assuming I am stuck with XGA, it follows that this laptop is incapable of going higher than 1024x768? It's a hardware problem, right? Can someone confirm this so I can stop trying to make it work? :)

---

### Post by Rocket2DMn on 2008-05-14
> **johnjreeve said:**
> I am having the same issues described in this thread, except with the Radeon Mobility 7500 video card. I looked in the tech docs that came with the Inspiron 5100 laptop and found this:

Maximum resolutions                  1024 x 768 at 16.8 million colors (XGA);
                                     1400 x 1050 at 16.8 million colors (SXGA+)
                                     1600 x 1200 at 16.8 million colors

First, how do I find out if the screen is XGA or SXGA?

Second, assuming I am stuck with XGA, it follows that this laptop is incapable of going higher than 1024x768? It's a hardware problem, right? Can someone confirm this so I can stop trying to make it work? :)

It's not a problem, it's just the capability of the monitor.  I don't know how to tell if your screen is XGA of SXGA, you would probably have to consult the specs on the computer, either whatever came when it was shipped, or by checking on dell.com.  From dell.com you may have an account registered with your computer, otherwise you can query the service tag and it should show you the original specs on the machine.  If all else fails you can call dell and they should be able to tell you once you give them the service tag.

---

### Post by MaxCapacitor on 2008-05-17
On my old Compaq Presario 1800T (w/ ATI Rage Pro LT) laptop I had the same resolution issue with Xubuntu 8.04. Ubuntu 7.04 and 7.10 would allow me to use my display's native resolution of 1440x1050 but upon reformat and fresh install of Xubuntu 8.04, I was only left with 800x600 or 640x480.

I managed to get it to work after searching through dozens upon dozens of search results in this forum.

The solution I found was typing in this into the terminal:
```
gksudo displayconfig-gtk
```
From there, I changed my monitor from "Plug and Play" to "Generic 1440x1050@60Hz" (because there wasn't a listing for my Compaq laptop display) and made adjusts accordingly.

Now my laptop display is running at it's native resolution... and it took me 2 days of searching through the forums and a good bit of trial & error.

Maybe displayconfig-gtk might work for your old laptop as well?

---


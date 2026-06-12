---
title: "Xserver.xorg configuration for Toshiba TE2100"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2007-10-03
Hi Guys,
I am totally dead. I tried downloading the nvidia driver and after that my X would not start. 
I tried editing my xserver-xorg by myself but I must have mis pressed something that now X is able to load but when it starts the screen goes blank (i think i must have screwed up the settings because it's similar to changing window's resolution and going blank when the resolution is too big)

I use a Toshiba TE2100 with NVidia GeForce4 420 Go. I do not have the installation CD with me right now, and I don't even know what the wizard is talking about throughout the entire set up so some help would be greatly appreciated.

Pls help me asap: I have a script written inside that I have to hand up tonight

(PS are there any articles that describe what each window means in the configure xserver-xorg wizard?)

[http://gentoo-wiki.com/HARDWARE_Toshiba_TE2100](http://gentoo-wiki.com/HARDWARE_Toshiba_TE2100)
here is a link to my laptop's profile

Regards

---

### Post by w4ett on 2007-10-03
I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by disappearedng on 2007-10-03
Thank you for that.
However, 
I am still facing a lot of problems following running Veta as my driver. 
When i boot into X, there's nothing on my desktop, and I can't connect to the internet ( I guess its kind of like safe mode). I can't go online and install envy. 

When i rebooted I return back to my black screen of death (wrong resolution perhaps?)

Is there anything i could do such as replacing the xserver.xorg with the original one?

---

### Post by disappearedng on 2007-10-03
Any Help??

---

### Post by disappearedng on 2007-10-04
Hi guys i have been able to open my xorg.conf and here is what it looks like:


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
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"ExplorerPS/2"
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
	Identifier	"Nvidia GeForce4 420 Go"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-40
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia GeForce4 420 Go"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

are there anything wrong with this???

---

### Post by disappearedng on 2007-10-04
Oh well I managed to solve the problem :)
My GDM was somehow disabled

---

### Post by coolcar on 2007-11-08
> **disappearedng said:**
> Oh well I managed to solve the problem :)
My GDM was somehow disabled

I have installed Gutsy Gibbon 7.10 on my Toshiba Satellite Pro TE2100.

Can you please shed some light in some high level language (english !) as to how did you get the nVIDIA drivers going for the TE2100?  I dont know what is GDM and id I have enabled it. I have tried unsuccessfully to install the restricted drivers via synaptic. I get the black screen after reboot. Then I have to rollback the driver to "nv" in xorg.conf to get X (GUI) going again. I also tried using the package "Envy" but that had the same result. 



1) Did you have to set the following option in /etc/X11/xorg.conf?  

```
option "UseDisplayDevice" "DFP"
```

or to disable the splash screen in GRUB?

```
nano /boot/grub/menu.lst
```
Use the arrow keys to scroll to the end of that line where you'll find where it says -ro -splash -quiet
Remove the word splash.
Ctrl+X to save, confirm the overwrite and reboot.


Well since you own the same model of laptop ( hopefully with same chip NV17 [GeForce4 420 Go] ) maybe it what ever you did will work for me. There is another[ thread]("http://ubuntuforums.org/showthread.php?t=582256") which discusses similar issue.

---


---
title: "Problem installing Ubuntu on HP-DV9575eo"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Fixel on 2007-09-21
Hi all!

I'm having trouble installing Ubuntu 7.04 on my HP DV9575eo laptop.

Specs: [HP DV9575eo](http://h10010.www1.hp.com/wwpc/se/sv/ho/WF06b/23355-186369-1291457-1291457-1291457-80247561-80478404.html?jumpid=oc_R1002_SESVC-001_HP%20Pavilion%20dv9575eo%20Notebook%20PC&lang=sv&cc=se)

When selecting install Ubuntu it loads for a while then gives me the following error:

[    30.9289051]   PCI: Failed to allocate mem resource #6:20000e0000000 for 0000:0


Side note: I had no problem what so ever in installing Mandriva (but I wan't UBUNTU!!!)

---

### Post by Sef on 2007-09-21
1) Did you md5sum the download?

2) Burn the iso at 4x or less?

3) Check the disk for errors?

---

### Post by Fixel on 2007-09-21
1) No

2) No - Does it have to be 4x or less?

3) No - Will check.

---

### Post by Dr Small on 2007-09-21
I never use MD5sums, because I never understood them, but I always burn mine on 1x and then check them for errors ;)

---

### Post by Fixel on 2007-09-21
Can't check the disc for errors it gives the same error-message as above... should I burn at 1x and retry?

---

### Post by dilia on 2007-09-21
Hi there,

I have a vaio (vgn-fz11s) and just yesterday I managed to install Ubuntu 7.04.

I still see this error message you've mentioned (about mem allocation failure)  during Ubuntu boot up, I'm guessing it has to do with the nvidia graphics card. 

Anyway, to installl ubuntu, press F6 to enable boot options, then one time the down arrow and then add this line: 

all_generic_ide

to the end of the command line and start the installation, that should do it (worked for me).

Hope it works!

---

### Post by Fixel on 2007-09-21
So can you boot it? 

PS. tried reburning the disc at 1x didn't work.. will try this in a couple of hours... time for my gf

---

### Post by Fixel on 2007-09-21
Ok, tried to boot using all_generic_ide this makes it continue booting. But It shows no picture at all (the screen isn't even black, it switches off).

Is it possible that I should use all_generic_sata (since my HDDs are sata)? Or is there something else I should try?

---

### Post by mysticmatrix on 2007-09-21
> **Fixel said:**
> Ok, tried to boot using all_generic_ide this makes it continue booting. But It shows no picture at all (the screen isn't even black, it switches off).

Is it possible that I should use all_generic_sata (since my HDDs are sata)? Or is there something else I should try?

The problem might be related to Nvidia 8600. As they were released after Feisty came, the default nv drivers can't recognise it. You can either
A) Try the Gutsy Beta, to be released in few days, which has better support for these cards
B) Try the text based installer. Start under Vesa, and then install the Nvidia drivers.

---

### Post by Fixel on 2007-09-21
Ok, since A can't be done at the moment then I'll go with B. Is there any guide on how to do this?

P.S. tried booting edgy just for the kick, didn't work gave me an x-server error.

---

### Post by mysticmatrix on 2007-09-21
> **Fixel said:**
> Ok, since A can't be done at the moment then I'll go with B. Is there any guide on how to do this?

P.S. tried booting edgy just for the kick, didn't work gave me an x-server error.
Ok lets go step by step
a)Install Ubuntu from Alternate CD
b) Reboot after installation is done. Xserver will crash, and you will be on command line
c) Login with your passward and username. (Password doesn't echos bach as *, just enter the correct passord)
d) Post output of command
```

cat /etc/X11/xorg.conf
```

Then we shall proceed further.

---

### Post by Fixel on 2007-09-21
This may be noobish, but...

I'm only seeing a part of the xorg.conf I can only see from

Subsection "Display" to section "DRI" 

how do I scroll up? Or what shoudl i do? :confused:

---

### Post by Fixel on 2007-09-21
Found way to scroll up copying now.. (by hand)

---

### Post by Fixel on 2007-09-21
OK solved it.

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled:"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled:"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcedfont-conf.d/dirs/TrueType"
Endsection

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
	Option		"XkbMode1"	"pc105"
	Option		"XkbLayout"	"se"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "Input Device"
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
Endsection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY


Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
Endsection

Section "Monitor"
	Identifier	"Allmän skärm" (note from fixel --> swedish meaning default/common/generic screen)
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Allmän skärm"
	DefaultDepth	16
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
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"cursor"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Fixel on 2007-09-21
And that's the xorg.conf

I have no idea how to edit it so plz teach me (if I need it).

---

### Post by mysticmatrix on 2007-09-21
> **Fixel said:**
> And that's the xorg.conf

I have no idea how to edit it so plz teach me (if I need it).

Ok so we have the data now

Once in Command Line, type

```
sudo nano /etc/X11/xorg.conf
```

This will open the text editor, nano

Now you have to edit this line

```
Section "Device"
Identifier "nVidia Corporation NVIDIA Default Card"
Driver "[COLOR="Red"]nv[/COLOR]"
BusID "PCI:1:0:0"
Endsection
```


to 

```
Section "Device"
Identifier "nVidia Corporation NVIDIA Default Card"
Driver "[COLOR="Red"]vesa[/COLOR]"
BusID "PCI:1:0:0"
Endsection
```

After this, save the file and restart your computer. This should land you to graphical interface.
Go ahead and tell the results.

Using Nano: Saving Document <ctrl>+<o>
Exiting <ctrl>+<x>

Nano is quite easy to use and self explainatory.

EDIT: This part is little education part. 
X server(or Simply X), is the method Ubuntu relies on to display the graphical system.
Most of settings of X server are found in file /etc/X11/xorg.conf file.
You see that X did realise that you have a Nvidia Card, it simply couldn't tell that it is 8xxx series.
Vesa is the failsafe driver. It is build upon certain standards, which all card manufacturer have decided to agree on. If nothing works, vesa provides a basic graphical display.
BTW, Gutsy includes "Bullet Proof X". Throw anything on Gutsy, it will always boot in graphical mode, and try to fix graphics problems.

---

### Post by Fixel on 2007-09-21
So when I've installed the nvidia drivers I should edit the xorg.conf to say "nv" instead of "vesa"?

If that's all then thank you very much for your help!

---

### Post by mysticmatrix on 2007-09-22
> **Fixel said:**
> So when I've installed the nvidia drivers I should edit the xorg.conf to say "nv" instead of "vesa"?

If that's all then thank you very much for your help!

No, you have to first change to vesa, get back the GUI, and then install the nvidia drivers. That would be a different story.
Have you got GUI back?

EDIT: When you have installed Nvidia drivers, your xorg.conf would be automatically changed to "nvidia". That's assuming you use Envy, which is by far most easiest and safe way to go by.[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Fixel on 2007-09-22
Yes got the GUI back gonna install nvidia drivers using envy soon. Will report back when I've done so.

---

### Post by Fixel on 2007-09-22
Ok, so I downloaded the envy .deb file from albertomilano.com/nvidia_scripts1.html and ran it. It gives me an error message when I click install:

"Please insert 'Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)' into the drive '/cdrom/'"

The disc is in the drive, but it doesn't appear on the desktop as usual.

From computer I can see it as "Cd-rom 1" but when I click to access it, it shows me:

"Cant mount the selected volume. 
mount: special device /dev/hda does not exist"

What should I do? :S

---

### Post by Fixel on 2007-09-22
OK, managed to install envy using instructions on [this](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu) page.

But it now says:

"You have 1 broken package on your system!

Use the "Broken" filter to locate it."

How do I fix this broken package?

---

### Post by Fixel on 2007-09-22
Tried the "sudo apt-get install -f" but then it tells me to insert cd and we're back to the problem of it not finding the cd/dvd-drive :(

---


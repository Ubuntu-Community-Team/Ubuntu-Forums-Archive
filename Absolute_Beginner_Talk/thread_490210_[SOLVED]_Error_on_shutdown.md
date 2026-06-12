---
title: "[SOLVED] Error on shutdown"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-07-02
Hi, I've been getting this very strange problem for a little bit now, it seems that the longer i use my ubuntu for the more cache memory gets used up - but it dosen't go down, it just keeps increasing to no end. I noticed this first when i install the system monitors, i've got one that views the CPU usage, and the other does the Memory.

The Cache memory just goes up and dosen't stop from boot up, the more programs i use, the higher it goes - but if i close down those programs it dosen't go back down, i don't understand why not, it's not how RAM should work right?

anyway i've also noticed that after long periods of use (and i'm not sure if this is all related) that once that cache goes up my programs start stuffing up - i can't open up new programs i just get no reaction, and my keyboard dosen't work any more - how can i fix this?

this happened just then and i went to shut down, i got the following error message upon shutdown. I clocked on the shutdown button, the screen went blank then it hung on this message until i physically pressed the restart button. i've seen this beofre but i wrote it down this time - 

```
<7> 2:0:0:0: shutdown
[7304.248000] Syncronizing SCSI cache for dick sdc:
[7304.248000] ide-disk 1.1: shutdown
[7304.248000] ide-disk 1.0: shutdown
[7304.248000] ide cdrom 0.1 shutdown
[7304.248000] ide cdrom 0.0 shutdown
[7304.248000] syncronizing SCSI cache for disk sdb
[7304.248000] sd 0:0:0:0: shutdown
[7304.248000] syncronizing SCSI cache for disk sda
[7304.248000] atkdb serio0: shutdown

```

i'm not sure if i took it down perfectly but that's pretty close - i can see it mentions cache, but it looks more like mainly references to my hard disks and ohter physical drives in that message.  I really don't know what's going on there to be honest - any help is much appreciated.

---

### Post by Beatbreaker on 2007-07-04
ok i did some reading about and found that the cache memory used is nothing to worry about - it'll be supplied to the system when it requires it. 


i'm still wondering why the kaybaord will stop working after a while of use - and also why i get that error message when the kaybaord stops workig also - it's not a normal shutdown so somehting is obviously wrong.

---

### Post by whizbaby on 2007-07-04
Your keyboard problem sounds like a graphics driver problem to me (maybe Im totally wrong though...). Just to exclude this possibility: what graphics card do you have and which driver are you using to run it? If its an nvidia, is composite explicitly turned off?(if not, try putting it to 'disable')

---

### Post by Beatbreaker on 2007-07-05
you may be right - I haven't set up the NVIDIA drivers on this instillation properley i don't think yet, i'm using the "restricted drivers" - "NVIDIA accelerated graphics driver" 

it's probably not the best of choices to get my drivers up and running but it just seems to work i'm on compiz fusion at the moment and it hasn't crashed on me once. 

i'm worried if i switch to the realy nvidia drivers something will stuff up like here:
[http://ubuntuforums.org/showthread.php?t=488145](http://ubuntuforums.org/showthread.php?t=488145)

admitedly all i had to do was change my xorg a little to get it to work but i never found out if changine the driver in xorg from "nvidia" to "nv" would be pulling the performance a little from it.

anyway my card is an NVIDIA 6600GT in an AGP slot

---

### Post by whizbaby on 2007-07-05
1-as you state yourself its not hard to fall back to the old configuration. Just backup your configuration file /etc/X11/xorg.conf (e.g. copy it to another name like /etc/X11/xorg.fallback) and if X doesnt come up you can still troubleshoot or load the old config.
2-nv is not the best choice, can cause 'unexpected problems' ... please try the nvidia-glx package and get help here if needed. Remember to put something like (in fact *exactly* like):

Section "Extensions"
        Option          "Composite"     "Disable"
EndSection

in your xorg.conf. And be sure not to have AllowGLXwithComposite or so turned on. Does the Problem still show up?  BEFORE you do all that install w3m (if not already on system, try w3m [www.ubuntuforums.org](www.ubuntuforums.org) in a terminal) to be able to surf the internet from console. ctrl-alt-F_KEY,
where F_KEY is one of the first eight function keys F1-F8 switches the virtual consoles created at boot time. When X doesnt show up, hit e.g. ctrl-alt-F1 to get a console and login. Your xserver runs on the seventh, so ctrl-alt-F7 will switch you back to graphical mode.

---

### Post by Beatbreaker on 2007-07-07
ok i'm a little concerned with playing around with my working vid card settings though to be honest. The error hasn't come up since i posted that message but i'll give what you suggested a go when i brace myself properley.

heres a copy of my xorg.conf for you to see, you might be able to find something with the video drivers there that looks weird.

```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "Buttons" "7"
    Option "ButtonMapping" "1 2 3 6 7"
    Option "Emulate3Buttons" "false"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"A201P1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"A201P1"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by whizbaby on 2007-07-08
I would try to put what I mentioned between the 'Monitor' and 'Screen' section. The reason is that on some nvidia cards (e.g. my gforce2) composite doesnt really work together with agpgart. I believe you would have to substitute it by nvagp, but this job is non-trivial (e.g. blacklilsting of agpgart doesnt work).

---

### Post by Beatbreaker on 2007-07-11
i tried adding this to my xorg.conf

```
Section "Extensions"
Option "Composite" "Disable"
EndSection
```

i stopped receiving 3d in my compiz fusion,  i then overwrote my xorg.conf doing something with the nvidia-glx drivers, i then couldn't get into ubuntu at all, i made a cp of the backup and now i'm back to how things were when i started posting when compizfusion worked 

- i don't know what you mean by "AllowGLXwithComposite" 

in my Xorg as i posted before i'm not using the "nv" drivers - i'm using the "nvidia" driver - nvidia-glx is already installed i can see it in my synaptec package manager. I'm not so sure i understand what you're trying to get me to do, my 3d card works, i've got compiz fusion working as stated above 

i haven't seen the problem since i posted it up here so i guess i'll just leave it go and it hopefully won't happen again - unless i'm really using the wrong 3d drivers and have to make more changes but everything seems to work ok with the video cards i think

---

### Post by whizbaby on 2007-07-11
Noprob, you didnt have AllowGLXwithComposite in your cards section, so it doesnt matter. Remember that composite on nvidia card running on agpgart may freeze. Compiz, of course, needs composite, so if you turn it off turn off compiz, too.

---

### Post by Beatbreaker on 2007-07-11
> **whizbaby said:**
> Noprob, you didnt have AllowGLXwithComposite in your cards section, so it doesnt matter. Remember that composite on nvidia card running on agpgart may freeze. Compiz, of course, needs composite, so if you turn it off turn off compiz, too.

ok i understand that - actually switching off composite in compiz fusion may be another thing i don't know how to do as of yet.



anyway i decided to go ahead and install the ENVY NVIDIA drivers - now i can't get into Ubuntu at all any more. i get the following message when trying to log in: -(not word for work but pretty close- i'm in Windows at the moment typing this up)

```
(EE)NVIDIA(0): Failed to initialize the NVIDIA kernel module! 
please ensure that there is a supported NVIDIA GPU in this system and the the NVIDIA device files have been created properley 

**aborting**
Screen(s) found bu none have a usable configuration
Fatal server error:
No screens found
```

i tried to use a backed up version of my xorg.conf but this hasn't worked for me this time - what's going on? should i edit the xorg.config and bring the drivers back to "nv" drivers now?

---

### Post by Beatbreaker on 2007-07-14
FIXED: see [http://ubuntuforums.org/showthread.php?p=3018722#post3018722](http://ubuntuforums.org/showthread.php?p=3018722#post3018722) post 194

---


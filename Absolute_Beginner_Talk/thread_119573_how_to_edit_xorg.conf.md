---
title: "how to edit xorg.conf"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by manosone on 2006-01-19
Hello to all.I am new in linux as you can see.Well..i have a "problem" with my screen resolution.It's not going over 1024x768.I have found that i have to edit xorg.conf.But i do not know how to edit.Could someone help me please?Moreover could someone give me a link to learn the command such as "ls",how to edit,how to make folders etc.Commands for the command line.Thank you.

---

### Post by aysiu on 2006-01-19
Try ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

---

### Post by dueY on 2006-01-19
ls just lists the files in the current directory
If you're using GNOME to edit a file you type ```
sudo gedit [file path]
```
To make a folder you use the mkdir command.

So to edit your xorg.conf you would type
```
sudo gedit /etc/X11/xorg.conf 
```
..assuming you are using GNOME.

---

### Post by ardchoille on 2006-01-19
ls = make a link
mkdir = make a directory
rmdir = remove a directory
rm = remove a file
cd = change directory
mv = rename a file

You can read the man pages for those commands and learn a great deal.

You can set up xorg.conf with the following command:

```

sudo dpkg-reconfigure xserver-xorg

```

Or, you can edit the file as root with:

```

sudo gedit /etc/X11/xorg.conf

```
Notice that in the above command, the "X" in X11 is upper-case.

---

### Post by Sutekh on 2006-01-19
[Terminal for Beginners by Kyral]("http://www.ubuntuforums.org/showthread.php?t=73885")

---

### Post by manosone on 2006-01-19
Well..pretty quick questions.Thank you.I have edit it but i can not see 1280x1024 in screen resolution.Am i wrong somewhere?In my first post about "ls",i mean that i need a lnk with the commands about command line such as mkdir ls and more in order to learn how to handle command line.

---

### Post by dueY on 2006-01-19
[QUOTE=manosone] i need a lnk with the commands about command line such as mkdir ls and more in order to learn how to handle command line.[/QUOTE]

Check out the link Sutekh posted!

---

### Post by manosone on 2006-01-19
Yes i did.Thank you.Does anyone can tell me if am i wrong to anything?

---

### Post by Sutekh on 2006-01-19
So you have edited /etc/X11/xorg.conf but still do not have 1280x1024 yet?

Could you copy and paste /etc/X11/xorg.conf into a post here?

---

### Post by manosone on 2006-01-19
Here it is..

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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"VMWare Inc [VMWare SVGA II] PCI Display Adapter"
	Driver		"vmware"
	BusID		"PCI:0:15:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VMWare Inc [VMWare SVGA II] PCI Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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



****EDIT.I am working it over vmware,and i had set vmware to stretch the window an d not to fit in my host pc resolution.No i have another problem.I can see it in 1280x1024 but there is a big black border over my screen.Can anyone help me more?
****EDIT 2.I just saw that the screeen resolution is 1024x768 and i an 1280x1024 but with black border around.Asap help me cause my eyes have started to be in pain.
****EDIT3.I wrote "sudo dpkg-reconfigure -phigh xserver-xorg" and i checked 1280x1024 but in screen resolution i can see 1024x768 as highest.I repeat that i have 1280x1024 but i have black border around my screen.

---

### Post by mishranurag on 2006-01-19
Hi!  I did have lots of problem with screen resolution and I was not able to fix it for long (Didn't have time either). My monitor could support 1280 x 1024, but I was not able to get it to that configuration. I tried reconfiguring xserver-xorg multiple time, all in vain.  Today I fixed it finally. When used the command to reconfigure the xserver-xorg, I made sure to choose none other screen resolution except the one that works for me i. e. 1280 X 1024 and this time, it did work :).  I reported it so that somebody else who might have this problem may find it useful. Looking UBUNTU at monitor's native resolution is a treat. It looks a lot cool.  Anurag

---


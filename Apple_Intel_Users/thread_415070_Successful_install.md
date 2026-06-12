---
title: "Successful install"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by magic-neophyte on 2007-04-20
**Graphics setup on Mac mini - Intel GMA950 screen high resolution 1680x1050**

Dear Ubuntuers,

Finally I have Ubuntu Feisty Fawn 7.04 working the way I want it, on a Mac mini 1.66GHz Intel Core Duo machine, with 512Mb of memory. Setting up /etc/X11/xorg.conf was a little tricky, but now I have glorious 1680x1050 resolution in X and 1024x768 on the command line (tty). Upon request I gladly divulge my means, so read on or see below.  

One question I still have: Is there any way to increase the resolution of the command line?

Note to all Apple owners: it really is possible, Linux on the Mac, but the learning curve for some might be steep. First note down every detail about the hardware you have (all the stuff in System Information). Then proceed to give Feisty Fawn 7.04 a try. Remember to use the md5sum command (in Terminal) to check the bootable ISO (CD Image file) that you download. Burn it using Disk Utility, carefully checking the options so it will burn a bootable CD. Back up all your data before starting installation. 

Use rEFIt to get your Apple machine to do multiple boot. It works fine for me and is pretty too!

**How to change the video graphics mode to widescreen on INTEL GMA950 graphics cards in the Mac Mini**

Okay, first make sure this solution is for you. Open a terminal ( Apps -> Accessories -> Terminal ). I am assuming you can work with your screen resolution, but it it not optimal. If you have a distorted image, try pressing control-alt-F1 (or F2). A text login prompt might come up more clearly, and you can often log in to a terminal session with your regular user name and password.

Type in at the prompt: lspci

Look for a line that reads: VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

(use shift-page up and page down to scroll through the text if it flooded the screen due to the big font)

If you don't see anything resembling this line, chances are this document is not what you're looking for. This documentation was written for inexperienced users and aims to be as clear as possible, as you may have already noticed.

You will need to download and install a tool called 915resolution. This can be automatically done by typing the command: sudo apt-get install 915resolution
( if you have not used apt-get before, apt-get cannot find the package and tells you so, you may need to update the package database, you can do this by typing: sudo apt-get update
(of course, I am assuming you have a working internet connection) )

After it installs type: sudo 915resolution -l
It will list all the video modes that the graphics controller inside the Mini is programmed to handle automatically. Widescreen modes are often not listed. You will need to pick a mode to overwrite with your own preferred mode.

( I have noticed some increased success in picking that mode which would logically be the second-best choice, as the next to optimal mode of operation for your monitor (information about this can be found in your monitors documentation, e.g. on the CD that came with your monitor, usually in a PDF-file or as HTML files.))

In my case, the mode value I overwrite is 3c, but 5c also works. To set it to 1680x1050 resolution at 60Hz, (because that is the default optimal resolution of my monitor) I typed: sudo 915resolution 3c 1680 1050
(write the mode and settings that you entered down on a piece of paper, you may need them later)

Now you can switch back to the graphical mode by pressing control-alt-F7 ( some people may need to patiently try all F-buttons to find out which one was assigned to it, as your monitor and graphics card may need some time to adapt its frequencies back to the graphical mode ) When you see the ubuntu login screen (or something pretty you replaced it with) press control-alt-backspace to restart the X server (the program that helps draw all those pretty windows and buttons) and login manager gdm. Sometimes the new resolution comes up beautifully.

However sometimes the X server really needs a kick in the butt and you need to erase its memory of your previous graphics modes completely and tell it to flip to only one single video mode and not try all kinds of others.

To do this, you will need to edit the xorg.conf file. You could do this if you're working in a terminal session by typing: sudo nano /etc/X11/xorg.conf

Find all the lines that run: Modes "1280x768" "800x600" etc. etc.
( In nano you can press control-w and search for the term: Modes )

Remove all the double-quoted modes behind every Modes statement. Replace them by that one video mode which you want. ( All my Modes lines read: Modes "1680x1050" )

You need to create a file that stores the 915resolution values if you want them to be applied every time at startup, so you will never have to bother with this again. To do this open a text editor ( at the prompt type: sudo nano /etc/default/915resolution ) and enter something like the following lines (these are my settings):

MODE=3c
XRES0=1680
YRES0=1050

( For you these lines would end in the number of that mode you overwrote earlier, you wrote it on a piece of paper, hopefully. )

Save the file under the name /etc/default/915resolution (press control-o in nano) and restart the computer (type: sudo reboot). Hopefully all will go well. If it doesn't then I still have one more trick up my sleeve, but I would need to do some more exploring. You can do so too by reading man pages or using the --help option. ( type: man 915resolution or 915resolution --help ) Linux is worth exploring, if you've never used the prompt, I urge you to check out the top program and learn what it can do to help you see what it happening inside your computer. The names of the programs you see can almost all be read about in the man pages by typing man <name> at the prompt. Once your prompt is set up, use control-alt-F buttons to switch between multiple viewscreens.

If you need to know how to set up the prompt resolution ( to 1024x768 ), let me know.

Good luck!

Magic Neophyte

---

### Post by Greywhind on 2007-04-21
I'm sure nobody remembers me, but back in the days of Dapper, I tried to install Ubuntu on my Intel iMac 17", and I could not get it to install correctly.

I'm here today to tell you that Feisty WORKS. With barely any trouble at all. And I'd like to thank anyone responsible for that. I don't know if any Ubuntu developers will read this, but if they do, they should know that I appreciate their work.

I had Fedora 6 installed before, and I removed its partitions for Feisty. Once I'd gotten past that, the install went very smoothly and without any difficult setup. My sound worked out of the box, as did the mounting of my Mac partition. Neither of these worked in FC6 by default. Installing the driver for my ATI x1600 was as simple as clicking one check box, which is a major improvement as well. ndiswrapper installed without a hitch, getting my wireless working. (Although NetworkManager doesn't seem to be working with it.)

So thank you, Ubuntu, for everything you've done for Intel Mac users.

---

### Post by matcram on 2007-04-21
to magic-neophyte

hi, could you share with us the the method you used to get the 1680 resolution to work. I've followed some howtos but none of them worked for me. Since i have a MacMini Core Solo i hope your method is going to work with my comp.

Thanks in advance,
Matthieu.

---

### Post by bigred3373 on 2007-04-21
> **Greywhind said:**
> I'm sure nobody remembers me, but back in the days of Dapper, I tried to install Ubuntu on my Intel iMac 17", and I could not get it to install correctly.

I'm here today to tell you that Feisty WORKS. With barely any trouble at all. And I'd like to thank anyone responsible for that. I don't know if any Ubuntu developers will read this, but if they do, they should know that I appreciate their work.

I had Fedora 6 installed before, and I removed its partitions for Feisty. Once I'd gotten past that, the install went very smoothly and without any difficult setup. My sound worked out of the box, as did the mounting of my Mac partition. Neither of these worked in FC6 by default. Installing the driver for my ATI x1600 was as simple as clicking one check box, which is a major improvement as well. ndiswrapper installed without a hitch, getting my wireless working. (Although NetworkManager doesn't seem to be working with it.)

So thank you, Ubuntu, for everything you've done for Intel Mac users.

how did you get the graphics to work what check box?

---

### Post by Greywhind on 2007-04-21
In System->Administration->Restricted Manager, I checked the box next to the ATI restricted driver and let it install, then restarted the computer.

---

### Post by bigred3373 on 2007-04-21
> **Greywhind said:**
> In System->Administration->Restricted Manager, I checked the box next to the ATI restricted driver and let it install, then restarted the computer.

which resolution did you use it installed but gave me an error   i am using the 1440x900 it works okay thanks that was easier then what i was trying to configure  all day long

---

### Post by magic-neophyte on 2007-04-24
Moved solution to top of the page for immediate viewing.

---

### Post by stephenkench on 2007-04-24
Hi

I have successfully install Feisty on a Intel mini mac which I am using as a MythTv frontend. I used a DVI to HDMI lead to feed the info into a Samsung 37" LCD TV using 1360x768 display.

The problem I have is that I can not play a DVD using Mythtv or VLC.
Using dmesg I see lot of read/seek errors.

If I reboot into Mac OX the DVD plays OK.

Has any one seen a similar problem?

Thanks
Stephen

---

### Post by ronocdh on 2007-04-24
> **stephenkench said:**
> Hi

I have successfully install Feisty on a Intel mini mac which I am using as a MythTv frontend. I used a DVI to HDMI lead to feed the info into a Samsung 37" LCD TV using 1360x768 display.

The problem I have is that I can not play a DVD using Mythtv or VLC.
Using dmesg I see lot of read/seek errors.

If I reboot into Mac OX the DVD plays OK.

Has any one seen a similar problem?

Thanks
Stephen
My initial response is that it's a codec issue, but if VLC doesn't have it, well, it doesn't exist! I would google around for dvd playback in vlc in feisty and see what crops up; might want to consider using Technorati. Multimedia forum might have more answers for you, too. Please don't forget to post back with what gets it going! =)

---

### Post by stephenkench on 2007-04-24
> **ronocdh said:**
> My initial response is that it's a codec issue, but if VLC doesn't have it, well, it doesn't exist! I would google around for dvd playback in vlc in feisty and see what crops up; might want to consider using Technorati. Multimedia forum might have more answers for you, too. Please don't forget to post back with what gets it going! =)

I am pretty sure that the problem is not codec based.

The kernel error messages seem to indicate a problem with the IDE driver. I will try booting from a liveCD (from another distro) and see if that works.

Stephen

---

### Post by smiles007 on 2007-06-07
I'm running Kubuntu on my intel mac mini and i did what you said magic-neophyte with the 915resolution thing, but i can't get it to stay when i turn off the computer i know you mentioned how to fix this in the post but i can't figure it out do i get gedit or something i tried that and entered gedit sudo nano/etc/x11.conf like you said but i keep getting errors can anyone help me?

---

### Post by ronocdh on 2007-06-07
> **smiles007 said:**
> I'm running Kubuntu on my intel mac mini and i did what you said magic-neophyte with the 915resolution thing, but i can't get it to stay when i turn off the computer i know you mentioned how to fix this in the post but i can't figure it out do i get gedit or something i tried that and entered gedit sudo nano/etc/x11.conf like you said but i keep getting errors can anyone help me?
The correct command is: ```
sudo gedit /etc/X11/xorg.conf
```Or you could use: ```
sudo nano /etc/X11/xorg.conf
```Remember to capitalize the "X."

---

### Post by smiles007 on 2007-06-14
ok i open the gedit file now and i get 




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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Cinema Displ"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Cinema Displ"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
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



But i don't see were i need to take out the other screen resolutions, and every time i shutdown and reboot the 1680x1050 resolution doesn't show up what am i doing wrong??

---

### Post by trevorcarpenter on 2007-08-29
Yee-haw! It works. 

Thanks for all your hard work in writing this post. This was the first thread, in two days of work, that finally made sense, and worked.

Thank you,
Trevor Carpenter

---


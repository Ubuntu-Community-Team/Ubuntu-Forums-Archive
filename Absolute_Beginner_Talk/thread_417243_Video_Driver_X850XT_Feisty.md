---
title: "Video Driver??? X850XT Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-04-21
I installed Ubuntu 7.04 on my computer with a PCIex16 Sapphire ATI Radeon X850XT.  I don't know what is wrong, but I am unable to use my video card fully.  In Windows XP, I can have my moniter (Dell P991) set to 1600x1200 and 85 Hz.  But, in Ubuntu, I can only have it set to 1024x768 and 60 Hz.  I would really like to be able to use my computer at 1600x1200, but I don't know how to do this.

I have tried Envy, with which I got an error.  I have tried doing stuff with the Ubuntu restricted drivers, and with ATI's drivers, and neither solved this problem.  I have tried changing the resolution using > sudo gedit /etc/X11/xorg.conf
which did nothing.

Here is part of my output of the above:
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

I would really like to solve this, does anyone have any ideas?
ugh
Thanks

---

### Post by igknighted on 2007-04-21
> **mdknaebel said:**
> I installed Ubuntu 7.04 on my computer with a PCIex16 Sapphire ATI Radeon X850XT.  I don't know what is wrong, but I am unable to use my video card fully.  In Windows XP, I can have my moniter (Dell P991) set to 1600x1200 and 85 Hz.  But, in Ubuntu, I can only have it set to 1024x768 and 60 Hz.  I would really like to be able to use my computer at 1600x1200, but I don't know how to do this.

I have tried Envy, with which I got an error.  I have tried doing stuff with the Ubuntu restricted drivers, and with ATI's drivers, and neither solved this problem.  I have tried changing the resolution using 
which did nothing.

Here is part of my output of the above:


I would really like to solve this, does anyone have any ideas?
ugh
Thanks

See in that file how the highest resolution there is 1024x768?  Add the desired resolution at the line for the color depth you want (probably 24).  As for the sync rate, change the respective lines in the "monitor" section.  You need to look up the values in your monitor's manual.

EDIT: that command simply opens the file so you can edit it yourself.  Also, don't use "sudo" with a GUI app like gedit, use "gksudo" instead.  Normally not an issue, but can get you into trouble at times.

---

### Post by mdknaebel on 2007-04-21
Like I mentioned before, that does nothing.  However, when I added 1600x1200 to *every* line, and turned off the restricted driver:'ATI accelerated graphics driver', (then only Atheros Hardware Access Layer is turned on) it did add 832x624 to the list of resolutions, but thats all.

Any Ideas?
Please Help!

---

### Post by igknighted on 2007-04-21
> **mdknaebel said:**
> Like I mentioned before, that does nothing.  However, when I added 1600x1200 to *every* line, and turned off the restricted driver:'ATI accelerated graphics driver', (then only Atheros Hardware Access Layer is turned on) it did add 832x624 to the list of resolutions, but thats all.

Any Ideas?
Please Help!

What if you used "sudo dpkg-reconfigure xserver-xorg" and answer all the questions there?  Choose advanced for the monitor configuration and enter your sync ranges manually.

---

### Post by mdknaebel on 2007-04-21
Hmm, that seems a bit advanced, I dont really know the answers to any of those questions.  Are there any drivers availiable? Anything else that I can do?

Thanks

---

### Post by livesys on 2007-04-29
Hi mdknaebel,

The bad new is that support for new and high-end ATI video card for Linux are quite bad.

The good new is that I also own an ATI Radeon X850XT PCIe card and I has found a few ways to make this usable for many Linux distros including Ubuntu.


First of all, you have two options of getting this to work:

1) Use ATI Proprietary Linux binary driver aka "fglrx"
2) Use the included open-source driver aka "radeon"

Option #2 is highly recommended as it is easier to setup and it is more compatible with eye-candy like Compiz, Beryl.  However, there are a few problems that required you to tweak a few things to get thing working correctly.

Most Linux distros with xorg version 7.x+ will correctly detect the videocard as R480 Radeon X850XT.  Unfortunately, for some strange reason, they will automatically select "ati" as the driver.  This will result in "No screen found" error and you getting kicked to text console :(  To get around this, you have to edit the xorg.conf file.  Most distros will have nano or vim editor which you can run by typing:

```

sudo nano /etc/X11/xorg.conf

Now you need to find the Section "Device" then change 

Driver "ati" 
to 
Driver "radeon"

Hit "Ctrl + x" and then "y" to save and exit nano


or

sudo vim /etc/X11/xorg.conf

Hit "Insert" key so you can edit the file

Now you need to find the Section "Device" then change 

Driver "ati" 
to 
Driver "radeon"

Hit "Ctrl + c" then "Ctrl + c" and type ":x" to save and vim

```

Now you can type "startx" and hopefully XFCE, GNOME or KDE will load...

* The only exception to the above is the Ubuntu 7.04 fiesty w/ xorg 7.2.  This is the only time when the Driver "ati" will actually work for the X850XT.


Now that you got into your favorite desktop environment, you will notice the second problem:
The screen resolution is 1024x768 and the refresh rate is 60Hz !  While LCD-owners maybe happy with this setting, those with CRT monitors will have bleeding eyes and pounding headaches :cry: ](*,)  The DCC function is not  working with X850XT so the computer is not able to communicate with your monitor to get  available screen settings information.

Ubuntu unfortunately does not include a fancy monitor configuration tool so it is time for some more xorg.conf editing :(  It is just a tad easier now since you can use graphical text editor.  You will need root permission to edit xorg.conf so start your favorite editor with sudo unless you already login as root.

For XFCE:
sudo mousepad  /etc/X11/xorg.conf

For GNOME:
sudo gedit /etc/X11/xorg.conf

For KDE:
sudo kwrite /etc/X11/xorg.conf


Now you need to find the Section "Monitor" then update the HorizSync and VertRefresh to a setting that your monitor support. In your case, a Google search for "Dell P991 specs" list this [page]("http://support.dell.com/support/edocs/monitors/p991/en/spec.htm").  With this info, you can update the xorg.conf to shows:

```

Section "Monitor"
Identifier "Generic Monitor"
    Option "DPMS"
    HorizSync 30.0-107.0
    VertRefresh 48.0-120.0
EndSection

```

This will allow you to use refresh rate other than 60Hz.  With that done, you will want to adjust the resolutions.  The Dell P991 specs site show the resolutions that the monitor support.  The X850XT support 16 and 24 bit depth so the Section "Screen" should look something like this:

```

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]"
Monitor "Generic Monitor"
Defaultdepth 24

SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

EndSection

```

* You should check Display Properties setting in Windows for other possible supported screen resolution/refresh settings.  You can even specify correct modeline setting in the Section "Monitor" once you collect all the information regarding your monitor.

Don't forget to save a copy of a working xorg.conf for future reference.

These info also may work for the ATI Radeon X800 PRO XL XT PLATINUM EDITION AGP PCIe ( X800PRO , X800XL, X800XT, X800XT PE )
and the  ATI Radeon X850 PRO XL XT PLATINUM EDITION AGP PCIe ( X850PRO , X850XL, X850XT, X850XT PE )

---

### Post by livesys on 2007-04-29
You can tweak the Section "Device" for better perfomace:

```

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
	Identifier    	"Videocard1"
	VendorName  	"ATI Technologies Inc"
	BoardName   	"R480 [Radeon X850XT Platinum (PCIE)]"
	Driver		"radeon"
	Option		"ColorTiling" "on"
	Option		"EnablePageFlip" "true"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffScreenPixMaps"
	Option		"RenderAccel" "true"
	Option		"DRI" "true"
	Option 		"AddARGBGLXVisuals" 	"True" 
	Option 		"DynamicClocks" "on"
	Option 		"DPMS"
	BusID      	"PCI:1:0:0"
EndSection


```

You may also need these for eye-candy:

```


Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "dri" # direct rendering
    Load "vbe"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection


```

---

### Post by mdknaebel on 2007-04-29
Wow, Thank you sooo much!!

That worked great, I have all the settings now for resolution and refresh rate

Thanks Again

---

### Post by djlysuc on 2007-05-14
Thanks, works a treat with my X800 ATI card as well.

---

### Post by Synthetik on 2007-05-16
Hi livesys,

  I have my "PCIex16 Sapphire ATI Radeon X850XT" card hooked up to my TV as well through the S-Video TV-out.  Do you know what I'd have to change in xorg.conf to get this working?

---

### Post by Talon2 on 2007-05-16
> **livesys said:**
> Hi mdknaebel,

2) Use the included open-source driver aka "radeon"

Option #2 is highly recommended as it is easier to setup and it is more compatible with eye-candy like Compiz, Beryl.  However, there are a few problems that required you to tweak a few things to get thing working correctly.

Most Linux distros with xorg version 7.x+ will correctly detect the videocard as R480 Radeon X850XT.  Unfortunately, for some strange reason, they will automatically select "ati" as the driver.

livesys, I agree with everything in your original post except this.  I'm pretty sure that "ati" is just a wrapper these days and it selects the proper driver for you.  In this case "radeon".  I think you will find changing ati to radeon is unnecessary.

I have a 9600 which basically falls into the same level of support in the radeon driver as does your x850.

Cheers.

---

### Post by gene74 on 2007-06-17
trying to do this guide but i am having some problems
basically when i get to the part editing the xorg files i do not have this 


Section "Device"
        Identifier        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver                "ati"
        BusID                "PCI:1:0:0"
EndSection


i have this

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

---

### Post by shae on 2007-06-17
> **gene74 said:**
> trying to do this guide but i am having some problems
basically when i get to the part editing the xorg files i do not have this 


Section "Device"
        Identifier        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver                "ati"
        BusID                "PCI:1:0:0"
EndSection


i have this

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

What would you like to do?

---

### Post by gene74 on 2007-06-17
trying to follow the guide so i can enable desktop effects .

---

### Post by shae on 2007-06-17
I belive that the 9000 is supported by the open source drivers.  Try changeing fglrx to ati and restart x.  Then post the results of ```
glxinfo |grep direct
```

---

### Post by gene74 on 2007-06-17
> **shae said:**
> I belive that the 9000 is supported by the open source drivers.  

How do i do that?

---

### Post by shae on 2007-06-17
> **shae said:**
> Try changeing fglrx to ati and restart x.  Then post the results of ```
glxinfo |grep direct
```

This is how.

Change fglrx in xorg to ati.  Then save and restart x/reboot.  then post the output of the code.

---

### Post by gene74 on 2007-06-17
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---


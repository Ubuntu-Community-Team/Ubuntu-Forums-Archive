---
title: "resolution Feisty need help"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-04-24
I had begun posting my questions in another thread, until I realized I wasn't being very polite to the original poster, and then my simple question wasn't really that simple.....

> You're config file is messed up. Replace everything beginning with the first 'SubSection "Display" ' to the last 'EndSubSection' with: 

```


SubSection "Display"
                Depth           1
                Modes          "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection 
        SubSection "Display"
                Depth           24
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection


```

I did all this, but I am still not having success.  I have a 	S3 UniChrome™ Pro Integrated Graphics Processor

Please advise
Thanks
:confused:

---

### Post by renzokuken on 2007-04-24
so whats the actual problem you are trying to solve? did you restart X after you made the changes? could you post your whole xorg.conf file?

---

### Post by tomcheng76 on 2007-04-24
Press Ctrl+Alt+Backspace to restart X server
or "startx" in terminal if your ubuntu are not in GUI mode

Here is the sample xorg.conf
[http://dev.gentoo.org/~fmccor/docs/xorg/xorg.conf/xorg.conf.html]("http://dev.gentoo.org/~fmccor/docs/xorg/xorg.conf/xorg.conf.html")

---

### Post by mkjarema on 2007-04-24
> **renzokuken said:**
> so whats the actual problem you are trying to solve? SORRY, I forgot to mention that, I am stuck at a 600x800 resolution 
> did you restart X after you made the changes?  yes
> could you post your whole xorg.conf file?

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
SubSection "Display"
                Depth          1
                Modes          "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth          4
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth          8
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth          15
                Modes          "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth          16
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth          24
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

thank you so much for trying to help me.

---

### Post by mkjarema on 2007-04-25
bump, still need help please

---

### Post by kvonb on 2007-04-25
Open a terminal from the accessories menu, (or press <ctrl><alt><f1> and login) to get to a virtual terminal, and type this lot:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```
It will re-write your xorg.conf and will give you the option to select the resolutions that it detects.

When it finishes, reboot (the simplest way).

You should now see the highest res you chose.

Also if your computer/video card has a TV output and you have that plugged into a TV, unplug it before rebooting.

---

### Post by renzokuken on 2007-04-25
also, what grafix card / chipset have you got?

you are using the 'vesa' driver which is very stable but basic. using the correct driver will improve performance and allow better resolutions

---

### Post by u.b.u.n.t.u on 2007-04-25
> **mkjarema said:**
> bump, still need help please

Hi, not to hijack, but check this out:

[http://ubuntuforums.org/showthread.php?t=422521](http://ubuntuforums.org/showthread.php?t=422521)

You have a well known problem.

Sorry I can't offer a solution. I don't know of one.

At best there are bandaid fixes - no proper fix until the process that does this is fixed so that it works as it ought to.

---

### Post by mkjarema on 2007-04-25
> **kvonb said:**
> Open a terminal from the accessories menu, (or press <ctrl><alt><f1> and login) to get to a virtual terminal, and type this lot:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```
It will re-write your xorg.conf and will give you the option to select the resolutions that it detects.

When it finishes, reboot (the simplest way).

You should now see the highest res you chose.

Also if your computer/video card has a TV output and you have that plugged into a TV, unplug it before rebooting.

Ok, now I have a problem.  I can't boot into the GUI.  I am using the kde desktop (I can't get it uniinstalled).
I get this error

```
bcm43xx:error:microcdode "bcm43xx_microcode5.fw" not available on load failed
```

and it just keeps erroring out.

now I also get this error when I am trying to run the puregnome commands too, it just keeps running this error.  I do not use my internal wireless card so i don't know how to get rid of this either.

So I need to get my screen back (any resolution at this point) and I need to get rid of that error

This is my card, unfortunatly I don't know the other details have a S3 UniChrome™ Pro Integrated Graphics Processor

this is getting very frustrated :(

---

### Post by u.b.u.n.t.u on 2007-04-25
```
bcm43xx:error:microcdode "bcm43xx_microcode5.fw" not available on load failed
```

I had the exact same problem. I think it relates to a bug in regards to a WiFi card.

I removed mine while unsuccessfully trying to fix the screen resolution, bit color and refresh rate.

After I removed my WiFi card, I didn't see this error again. Hardly a solution I know.

All the best.

---

### Post by mkjarema on 2007-04-25
> **u.b.u.n.t.u said:**
> ```
bcm43xx:error:microcdode "bcm43xx_microcode5.fw" not available on load failed
```

I had the exact same problem. I think it relates to a bug in regards to a WiFi card.

I removed mine while unsuccessfully trying to fix the screen resolution, bit color and refresh rate.

After I removed my WiFi card, I didn't see this error again. Hardly a solution I know.

All the best.

my card is internall, i can't physically remove it, is there a code to inactivate it?

---

### Post by u.b.u.n.t.u on 2007-04-25
> **mkjarema said:**
> This is my card, unfortunatly I don't know the other details have a S3 UniChrome™ Pro Integrated Graphics Processor

this is getting very frustrated :(

My guess is that the problem relates more to your monitor than your GPU (Graphics Processing Unit), (Video Card).

Your xorg.conf lists yours monitor and GPU as generic. Not a good thing as default settings are being used and Ubuntu at present doesn't handle this properly.

The best you can hope for is a lock in to a specific screen resolution and refresh rate. That needs to consist of your monitor details as the horizonal and vertical refresh rates need to be edited into the xorg.conf.

So basically, do you know what monitor model you have? From there one needs to find the specs and the refresh rates, something like this:

```
Section "Monitor"
	Identifier	"G90f+"
	Option		"DPMS"
        HorizSync       30-97 
        VertRefresh   50-180  
EndSection
```

---

### Post by kvonb on 2007-04-25
The bcm43xx:error is something to do with your wireless adapter, so I can't help you there unfortunately.

As for getting a desktop back, boot into recovery mode, (press esc at boot if you don't get a menu).

Then type:

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

It will walk you through the x setup, for your graphics card, select "Savage" from the options list that you will see.

Then reboot and hopefully you will have a desktop again :).

---

### Post by u.b.u.n.t.u on 2007-04-25
> **mkjarema said:**
> my card is internall, i can't physically remove it, is there a code to inactivate it?

Sorry, not that I know of.

 It appears that if drivers could be found that would solve it. 

I am unsure where to halt error reporting in Fiesty Fawn. If someone knows that would help.

---

### Post by mkjarema on 2007-04-25
> **kvonb said:**
> The bcm43xx:error is something to do with your wireless adapter, so I can't help you there unfortunately.

As for getting a desktop back, boot into recovery mode, (press esc at boot if you don't get a menu).

Then type:

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

It will walk you through the x setup, for your graphics card, select "Savage" from the options list that you will see.

Then reboot and hopefully you will have a desktop again :).

i was able to run that command, but when rebooting i get caught up on the wifi error refrenced earlier in the post.  I still have desktop :(  Thank you

I am starting another thread right now to inactivate that wifi "thing"

---

### Post by hatstand on 2007-04-25
OK, I have been following this and other threads about the screen resolution, and am now officially hacked off. So hacked off, in fact, that I am at this moment, downloading SimplyMepis. 

My work computer uses some old rubbish monitor (Benq V551, if you're interested) and, like many, I am locked in 800*600 mode. I have tried 
"sudo dpkg-reconfigure xserver-xorg"
then
"sudo dpkg-reconfigure -phigh xserver-xorg"
then
"sudo gedit /etc/X11/xorg.conf" (here is the relevant bit of xorg.conf)
[I]
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa" 
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-54
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection[/I]

You will see that I have not specified 800*600 AT ALL, but that, and 640*400 is all I get. I am fed up with this. Edgy worked fine. Is this a case of "must release Feisty because it's been 6 months, even though it's not ready"?

AAAAaagggghhhh!!!!!!

---

### Post by u.b.u.n.t.u on 2007-04-25
A good post hatstand. I hear you.

I personally would not use a different distro. I like ubuntu too much.

I do know that I will be assisting to resolve this as I have volunteered for such and am in contact with the person who has been assigned to this.

Enjoy the other Linux, but keep an eye on Ubuntu.

Yes they have stuffed up, but they are still worth it because they will fix it... I at least hope so.

I have already lodged files for review and the problem is basically known.

It is my understanding that by the time Gutsy Gibbon is released, that this problem is resolved.

Ubuntu needs to query the monitor for horizontal and vertical refresh rates. Then provide options based on the power of the GPU. Pretty straight forward but when it fails to do this it guesses, and the guesses are wild and just don't work as you and I know.

So basically that the problem as I understand it.

Now some very bright people will sort this I hope.

---

### Post by maruchan on 2007-04-25
Hatstand, why are you using VESA? Don't you have a video card installed?

---

### Post by kvonb on 2007-04-25
Seeing as you both have that bcm43xx problem, I guess that's the clue.

Can you disable or remove the wireless device just to see if it makes a difference?

---

### Post by u.b.u.n.t.u on 2007-04-25
> **kvonb said:**
> Seeing as you both have that bcm43xx problem, I guess that's the clue.

Can you disable or remove the wireless device just to see if it makes a difference?

I physically removed my WiFi, PCI card and didn't receive the error message anymore. So it seems that error message is related to Ubuntu's inability to find a suitable driver.

---

### Post by hatstand on 2007-04-25
Thanks for the replies, guys. I just had to let off steam after 4 days of tinkering with refresh rates, xorg.conf and xserver stuff

As for why am I using vesa, I don't know what video card I have (the computer I am using at work is  a "BlueCode" ??? and I can't find the specs. I know there is a code line for finding it, and I will look it up here and try to change the driver. i did try about 4 of them at random, and none worked: when I am working to deadlines and having to restart all the time, it gets very frustrating. Will let you all know.

I love Ubuntu and have been trying to convince work mates to switch to open source. This has not helped my case.

---

### Post by kvonb on 2007-04-25
> **hatstand said:**
> Thanks for the replies, guys. I just had to let off steam after 4 days of tinkering with refresh rates, xorg.conf and xserver stuff

As for why am I using vesa, I don't know what video card I have (the computer I am using at work is  a "BlueCode" ??? and I can't find the specs. I know there is a code line for finding it, and I will look it up here and try to change the driver. i did try about 4 of them at random, and none worked: when I am working to deadlines and having to restart all the time, it gets very frustrating. Will let you all know.

I love Ubuntu and have been trying to convince work mates to switch to open source. This has not helped my case.

try:

```
lspci | grep VGA
```

that should tell you the make/model

---

### Post by kvonb on 2007-04-25
> **u.b.u.n.t.u said:**
> I physically removed my WiFi, PCI card and didn't receive the error message anymore. So it seems that error message is related to Ubuntu's inability to find a suitable driver.

Yes, I read somewhere that they had to compromise on one of the libs, not sure which, but it was something to do with suspend in laptops.

Some stuff was left out, I know that some scanners and USB wireless device support was hosed by that decision.

My Netgear wg111 adaptors don't even show up in the USB device list, and I threw out my perfectly good scanner because Feisty didn't recognise it, when it has done since Breezy!

It might be related to that.

All you can do is wait until they release a fix, or go back to Edgy I expect.

---

### Post by hatstand on 2007-04-25
OK. looked up my video card, using lspci | grep VGA. Thanks kvonb.

I have a prosavage8. I tries the S3 and savage drivers: S3 returns an xserver crash. Savage driver makes no difference: still locked in to 600*800.

Oh well

---

### Post by kvonb on 2007-04-25
All I can suggest is downloading and booting the older CD, maybe 6.06 or 6.10 to see if that works on a live boot.

I know it's not much to go on, and it will take a while to get down, but it might just save your sanity.

Or as u.b.u.n.t.u said he was going to do, try SimplyMepis.  If it works for him it might be worth a try.

---

### Post by hatstand on 2007-04-25
yep. As we speak, I am installing 6.10. I am using the live CD. 

Decided against Mepis. I hust ***like*** Ubuntu, and I reckon this, being a known bug, will be fixed in a week or two. I'll upgrade again, then. 

It's only work anyway. Kubuntu works perfectly at home.

Cheers for your help, kvonb

---

### Post by kvonb on 2007-04-25
I just had another idea:

Press <alt><f2> and type this into the pop-up:

```
gksu gedit /var/log/Xorg.0.log
```

Scroll down the page and look for something like this:

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.01.26.00
(II) NVIDIA(0): Detected AGP rate: 2X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 MX/MX 400 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0): Proview (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (87, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
```

That is from my spare computer and as you can see I am using an Nvidia Geforce 2/MX400.

Notice the part about "Validated modes", it also might give you some other clues as to what is going on, as in the driver that you are using.

Maybe even post that file here for us to have a look at.

Regards, Kev :)

---

### Post by kvonb on 2007-04-25
Damn, a day late and a buck short :(.

Oh well, maybe u.b.u.n.t.u will see this and post his.

It would be nice to get a line on this problem.

---

### Post by hatstand on 2007-04-25
Shame. Would have tried that. Unfortunately, I have work to do today. May try with my laptop, if it shows the same problem.

---

### Post by u.b.u.n.t.u on 2007-04-25
> **kvonb said:**
> Or as u.b.u.n.t.u said he was going to do, try SimplyMepis.  If it works for him it might be worth a try.

I never said that. Rather the opposite. I will either use XP or Ubuntu. I won't consider using a different Linux. Ubuntu or no Linux at all.

---

### Post by kvonb on 2007-04-26
> **u.b.u.n.t.u said:**
> I never said that. Rather the opposite. I will either use XP or Ubuntu. I won't consider using a different Linux. Ubuntu or no Linux at all.

Well then I must be mistaken, I thought you said that in your other "rant" thread.

---

### Post by hatstand on 2007-04-26
'twas me. I was so frustrated that I actually downloaded Mepis. It's hanging around as an iso in a backup folder somewhere now.

---


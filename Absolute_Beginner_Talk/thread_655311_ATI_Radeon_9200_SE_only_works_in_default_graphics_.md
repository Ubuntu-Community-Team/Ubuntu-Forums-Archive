---
title: "ATI Radeon 9200 SE only works in default graphics modes"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by beachedwhale on 2008-01-01
I installed Ubuntu 7.1 a couple of days ago. It went pretty well except for the graphics issues.  The default install automatically used default monitor, screen and driver for everything.  Refresh rate is 61Hz and resolution 1280x1024 (which is what I want for resolution), but with the default drivers everything just looks rather "blah".  Its usable, but pictures and video look bad, and I won't even try using anything that wants advanced graphics acceleration.

My monitor is a 19" Hitachi CRT, and graphics card is ATI Radeon 9200 SE that worked fine for Windows.  I ran a command to force it to redetect and generate a new xorg.conf file.  It successfully redetected, and correctly (or so I think), everything.  But, after rebooting the video is scrambled... looks exactly like a scrambled analog cable TV channel.  (What would cause that?)  Switching back to the original xorg.conf file gets me working again.  

I then tried making manual edits based on the xorg.conf file that was created by the redetect.  If I ONLY change the monitor info, I get scrambled screen again.  If I only change the drivers to ati, I get scrambled again.  

I haven't tried downloading other drivers or doing anything else, since it looks like it has that stuff already by default but just isn't working.

I have no idea what's going on here.  How do I diagnose this?  Posted below are two versions of xorg.conf, first the working generic one, followed by the nonworking redetected one.  I removed the input device sections for brevity.

Working:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection



NOT WORKING:

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"CM751"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Monitor		"CM751"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768"  "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


Thanks!

---

### Post by llamakc on 2008-01-01
Have you tried installing the fglrx driver yet? If you want to use the stock ati (or radeon) driver, Try changing it to "radeon" and commenting out the below by adding a # at the beginning of the line.

# Option		"UseFBDev"		"true"

I have a different card, but here's what mine has:

```

Section "Device"
        Identifier        "ATI Technologies Inc Radeon rv370"
        Driver                "radeon"
        BusID                "PCI:5:0:0"
        Option          "XAANoOffscreenPixmaps"
#        Option "AGPMode" "4"
#        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection

```

And I added an AIGLX option at the end.

---

### Post by beachedwhale on 2008-01-01
I didn't try installing fglrx driver yet.  (Is it already there when 7.1 is installed?  How would I tell?)  What's the best way to get started doing that?  Going to ATI web site had some drivers for "Linux", but it wasn't readily apparent what I was supposed to do with it.

---

### Post by beachedwhale on 2008-01-01
I got my hopes up when I found this page:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But then it says this:

> Make sure the following things are true about your video card:
      The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.

Well, mine's the 9200.  Now what?  Then it says this:

> Note that if you own an ATI card from the R400 series or below, you already have working 2D and may have accelerated 3D with the default drivers. These cards include:
R200 and R100 series (9200 and below)

What does "may have" mean?  How do I tell?

---

### Post by bluebrew on 2008-01-01
I'm having issues with my ATI 9250 se Driver as well
hopefully we get a fix
I need a some assistance/instructions for a fix as well

[http://ubuntuforums.org/showthread.php?t=655074](http://ubuntuforums.org/showthread.php?t=655074)

---

### Post by beachedwhale on 2008-01-01
Despite the info on the howto page, I proceeded with what was on it anyway.  I get as far as this:

sudo aticonfig --initial 

This core dumps, and leaves me with a missing xorg.conf file (which I manually restored).  I rebooted and tried again.  Same thing -- core dump.

I also tried this command:

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

I'm not sure what that's trying to tell me.

---

### Post by highfructose327 on 2008-01-01
BinaryDriverHowto/ATI
[HTML]https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b[/HTML]

The Radeon open-source driver (ati)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

an archived forum on your card
[HTML]http://ubuntuforums.org/archive/index.php/t-594353.html[/HTML]

Envy is another solution it will detect,download and intsall  the drivers needed
here is the website:
[HTML]http://albertomilone.com/nvidia_scripts1.html[/HTML]

or the code to install envy 
```
sudo apt-get envy
```

there is alot of info on ati cards out there, hope it helps 
good luck

---

### Post by beachedwhale on 2008-01-01
I also tried this.  System->Administration->Screen and Graphics.

This brings up the Screen and Graphics Preferences. It defaults to "vesa".  I select "radeon" and press Test.  Again, scrambled screen.  When it returns from that, it says it "Configuration test failed" and "Please verify the selected devices and configuration."  I have no idea what its asking me to "verify" -- I chose "Radeon", what else more could I do?

This is very frustrating.  I have a pretty modern computer and a fairly common and recent type of card.  I have 15 years of Unix (not Linux) software development experience.  But, I can't figure this out.  I REALLY want to switch fully over to Linux in order to avoid the otherwise inevitable Vista downgrade.  But stuff like this leaves me SOL.

---

### Post by beachedwhale on 2008-01-01
~$ sudo apt-get envy
E: Invalid operation envy

HUH?  What's "E"?

---

### Post by highfructose327 on 2008-01-01
Envy is in  System> adminstration>synaptic package manager also. I will see if I can tell you what the error is

---

### Post by Don1500 on 2008-01-01
Please try ENVY, it does what you want it to. This will save you hours of frustration.

Here's the link: [[COLOR="Red"]Envy[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by beachedwhale on 2008-01-01
I tried the envy thing and it was going well until I tried to automatically install the ATI driver.  It failed, and this was in the log:

python pulse.py ati
Envy - Version 0.9.9
Ubuntu Gutsy 32bit
Your graphic card has been detected as a ATI Radeon 9250/9200 Series
Your graphic card is supported by the legacy Driver
ENVY ERROR: ATI's legacy driver does not support your operating system

---

### Post by highfructose327 on 2008-01-01
the error was it did not know what to do i.e. install 

```
sudo apt-get install envy
```

---

### Post by highfructose327 on 2008-01-01
I would try the Radeon Open source driver, that is what I am using I have ATI as well

---

### Post by beachedwhale on 2008-01-01
I tried the envy install again, but this time I selected manual.  It listed 3 versions, with the earliest version being the default for some reason.  That seemed wrong to me, so I selected the latest 8.4* something.  It spent a few minutes doing stuff.  What it logged showed a few errors but it otherwise claims it completed successfully.  When I rebooted, I got the dreaded message "Ubuntu is in low resolution mode".  I pressed Continue, and they weren't kidding... this mode is much worse than the default generic drivers I got.  What's more, my wifi card stops working for some reason.  Restoring the xorg.conf file fixes both the low res mode as well as my wifi card.

I've seen this happen before with the wifi not working when I'm in this low res mode.  What's up with that?  There's no wifi stuff listed in xorg.conf, so why does restoring it fix the wifi?  And when I say "not work", it completely disappears from the network control panel.  Ethernet is still there, but I can't string a 100' long CAT5 cable across the house... cats will eat it (something about the softness of a CAT5 cable they just LOVE to eat).

As for "Radeon Open source driver", can you point me to what'd get me started with trying that?

Thanks.

---

### Post by beachedwhale on 2008-01-01
Oops never mind about the Radeon Open source driver, I see you posted that earlier.  I'll see what I can do with that.

BTW, for future reference, should I ever decide to replace the graphics card, what is THE card that's the most guaranteed to work GREAT under Ubuntu?  (And with a LCD display connected via the digital video.)

---

### Post by highfructose327 on 2008-01-01
Nvidia is well supported, not sure what exact card to recommend. search Nvidia in the forums and I am sure you will find some good info

---

### Post by highfructose327 on 2008-01-01
From the unofficial ATI wiki [http://wiki.cchtml.com/index.php/Hardware]("http://wiki.cchtml.com/index.php/Hardware")

 > RADEON Legacy

    These cards are no longer actively supported by AMD as of the 8.28.8 fglrx driver. The installer is still available on AMD's website. ati-driver-installer-8.28.8.run 
    If you own one of these cards, it is highly recommended that you use the "radeon" open source driver. 

    * Radeon 8500
    * Radeon 9000
    * Radeon 9200
    * Radeon 9250 

Like llmakc said if you have problems with open source driver change the driver name in your Xorg.conf from "ati" to "radeon" 
good luck

---

### Post by beachedwhale on 2008-01-01
I went through the open source driver instructions and did them.  Same thing... scrambled screen.  I also tried "radeon" instead of "ati", but still scrambled screen.

I appear to have tried every suggestion, yet they all result in either a scrambled screen, or low-res mode.  Maybe something else is going here, but without having a detailed knowledge of the internals of Linux, I'm at a loss to suggest anything to myself.

I'd rather not try another video card either, since that might not be the problem.  What if I bring it home and the same thing happens?

---

### Post by llamakc on 2008-01-01
Go to the 2nd tty by hitting CTRL-ALT-F2. Login as your user.

Type

```

sudo dpkg-reconfigure xserver-xorg

```

Chose radeon for the driver, enter your card's PCI identifier, chose the specs for your monitor, et cetera.

Restart the X server by hitting ctrl-alt-backspace or starting it with:

```

sudo /etc/init.d/gdm start

```

---

### Post by beachedwhale on 2008-01-01
That reconfigure is the first thing I tried after the initial install.  Same thing: scrambled screen.

The only straws left to grasp at is that lspci shows two entries for my video card; I'm not sure what the second one is so I went with the default (1:0.0 instead of 1:0.1).

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

Also, I have no idea what the refresh rate range for my monitor is.  I'm not sure if that'd scramble the screen if the wrong values are in there?  Its 10 years old so I have no manual, and Hitachi won't put them online.

I haven't looked to see if my video card is flash upgradeable; is that worth trying?

> **llamakc said:**
> Go to the 2nd tty by hitting CTRL-ALT-F2. Login as your user.

Type

```

sudo dpkg-reconfigure xserver-xorg

```

Chose radeon for the driver, enter your card's PCI identifier, chose the specs for your monitor, et cetera.

Restart the X server by hitting ctrl-alt-backspace or starting it with:

```

sudo /etc/init.d/gdm start

```

---

### Post by DishBreak on 2008-01-01
> **highfructose327 said:**
> Nvidia is well supported, not sure what exact card to recommend. search Nvidia in the forums and I am sure you will find some good info

I'm running a Geforce 6200 on my desktop, works great. 
I had the 9200 initially, ended up replacing it because it wasn't worth the time for me to fix it. 

best of luck!
DishBreak

---

### Post by beachedwhale on 2008-01-01
Doesn't look like I can flash upgrade the graphics card... nothing on ATI's web site.

---

### Post by llamakc on 2008-01-01
What's the make/model of your monitor? What rates are currently set in /etc/X11/xorg.conf?

In fact, post the entire contents of your xorg.conf please, and the output of /var/log/X.org.0.log (inside of the code brackets).

---

### Post by highfructose327 on 2008-01-01
quote pixelnate

>  Hitachi CM751 monitor that are capable of 1280x1024 @ 85Hz

not sure if this helps

---

### Post by llamakc on 2008-01-01
```

Section "Monitor"
        Identifier      "Generic Monitor"
#       Option          "DPMS"
        HorizSync       31-93
        VertRefresh     50-160 
EndSection

```

Is supposed to work. Also, what color depth are you attempting to run at? Perhaps changing that to 16 instead of 24 will fix you right up? Have you tried that yet?

---

### Post by beachedwhale on 2008-01-01
Its a Hitachi SuperScan Elite 751, 19".  This was quite a spectacular monitor back in its day.  I'd replace it but the darn thing just won't quit working well!  (How dare they!)

I could try swapping with my new LCD monitor that's on the other computer.  If that one works, I'm not sure what that's telling me though.

Should I attempt to replace the graphics card, the cheapest one at Circuit CIty is: EVGA e-GeForce FX 5200 Video Card.  Should that one work by default without any extra configuring?

85Hz doesn't really help because there's both horizontal and vertical.

---

### Post by beachedwhale on 2008-01-01
The last non-working xorg.conf file (using the open source drivers) is:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Radeon 9200"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-93
	VertRefresh	50-87
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9200"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
	Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


I'm having trouble attaching Xorg.0.log (says invalid file).

---

### Post by llamakc on 2008-01-01
Your vertical refresh can be higher. See my above post. That was from somebody's working xorg.conf for your monitor version.

---

### Post by xeth_delta on 2008-01-01
I am sorry if I am repeating something already mentioned in the thread. Have the people that have problems with the "ati" driver given the "radeon" driver a try? That seems to have worked for others.

Happy new year!
Xeth

---

### Post by beachedwhale on 2008-01-01
radeon instead of ati made no difference.

I'm going to try swapping monitors... once my wife lets me (she's using it).  But if that actually helps, its not a solution since I can't permanently swap them.  My intent was to set up Ubuntu on the old hardware, not the new hardware.

(This Ubuntu is otherwise running really fast on old hardware.  Makes Windows hang its head in shame.)

---

### Post by highfructose327 on 2008-01-01
question about the 5200 geforce was dicussed at this forum link

[HTML]http://ubuntuforums.org/archive/index.php/t-84641.html[/HTML]

---

### Post by highfructose327 on 2008-01-01
beachedwhale  I picked up a used monitor at a thrift store for 10.00 usd. if the monitor swap works that my be a cheaper option than a new video card. I had also looked on ebay for graphics cards there were a few deals. Good luck

---

### Post by beachedwhale on 2008-01-01
When I look around for this Geforce 5200, I see both PNY and eVGA prefixes of the description, with the PNY ones costing twice as much.  What's up with that?  Did one company buy the other and there are different versions of this card out there?  I want the cheapest, as long as it works well.  Circuit City price is $37 with free (and slow) shipping; that's the cheapest I've found without trying eBay.

I'm still waiting to try a monitor swap.

---

### Post by bluebrew on 2008-01-01
> **beachedwhale said:**
> I tried the envy thing and it was going well until I tried to automatically install the ATI driver.  It failed, and this was in the log:

python pulse.py ati
Envy - Version 0.9.9
Ubuntu Gutsy 32bit
Your graphic card has been detected as a ATI Radeon 9250/9200 Series
Your graphic card is supported by the legacy Driver
ENVY ERROR: ATI's legacy driver does not support your operating system


Hi beachwhale,seems we are have the same problem
I had the same error as you had above when using ENVY
My pc is running in low graphics mode too,gonna tinker around some more after work,hopefully we can get these fixed

---

### Post by bluebrew on 2008-01-01
So does anybody know what this error is and how to fix it: 
python pulse.py ati
Envy - Version 0.9.9
Ubuntu Gutsy 32bit
Your graphic card has been detected as a ATI Radeon 9250 Series
Your graphic card is supported by the legacy Driver
ENVY ERROR: ATI's legacy driver does not support your operating system

I also cannot open my restricted driver manager?

---

### Post by beachedwhale on 2008-01-01
I can't open the restricted drivers manager either, says "Your hardware does not need any restricted drivers".  I'm not sure what that means, but I figured it was OK and proceeded anyway.

---

### Post by beachedwhale on 2008-01-02
I just tried my Samsung 22" LCD monitor with this.  Using the default drivers that worked with the old CRT, it looks much better (although stretched left-right due to the widescreen); this looks better simply because the Samsung is a terrific monitor.  However, it is still not being used to its full potential unless I can solve the video card problem.  Plus, it'd be impossible to change the resolution to fit the wide screen.

I let it autodetect again with the Samsung connected.  It autodetected fine, but when I restart X I have the identical problem -- scrambled video.  I was using the analog cable and didn't bother trying the digital cable to see if that mattered at all.

Unless anyone has any other ideas, I seem to be out of options except to buy a new video card and HOPE that actually works.  (Ever try to return a perfectly fine video card?  Retailers hate that.)

---

### Post by w4ett on 2008-01-02
I seem to be getting in late on this conversation, but I run several 9200SE cards and have had no problems at all with them, even while using Compiz Fusion....BUT I use them on CRTs.   My xorg.conf is as follows:

> w4ett@w4ett-desktop:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL E773c"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Monitor         "DELL E773c"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
w4ett@w4ett-desktop:~$ 

---

### Post by Yellow Pasque on 2008-01-02
FX5200? Yeesh.. 2003 called and it wants its video card back.
Try and find a nice, passively-cooled 7300GS. Or at least [this](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106&CatId=318) 6200, which is about the same price as the 5200.

EDIT: Even cheaper at ZZF ($30 after MIR). It's out of stock at the moment, but the rebate is good until the end of January.

---

### Post by beachedwhale on 2008-01-03
That 6200 looks reasonable enough.  I didn't realize it had DVI.  I'll probably order one of those.  Thanks.

---

### Post by beachedwhale on 2008-01-09
The 6200 arrived today.  I booted up with it.  Upon logon, everything still looks the same as before (good -- I was worried I'd get a blank or scrambled screen), then it gives me a dialog saying that it needed to install the restricted nvidia drivers.  I agreed, it did so, then it told me to reboot.  I did so, and upon rebooting it went into low res graphics mode again.  REALLY low res graphics too, 640x480 (at least I was at 1280x1024 before).  This is AWFUL, much worse than before.

It doesn't let me configure it to something other than VESA.  That "envy" thing fails when I try it, and the log has this error:

----- begin log -----
more envy-installer.log 
python pulse.py nvidia 
root@snowball-desktop:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.9
Ubuntu Gutsy 32bit
Your graphic card has been detected as a GeForce 6200
Your graphic card is supported by the latest driver
OK: All the packages are installed
Checking the Dependencies for the New Method
ENVY: The following packages are not installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  comerr-dev libatk1.0-dev libaudio-dev libbeecrypt6 libcairo2-dev
  libcupsys2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgcrypt11-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev
  libgnutls-dev libgnutlsxx13 libgpg-error-dev libice-dev libjpeg62-dev
  libkadm55 libkrb5-dev liblcms1-dev liblzo2-dev libmng-dev libneon25
  libopencdk8-dev libpango1.0-dev libpng12-dev libpopt-dev libqt3-headers
  libqt3-mt librpm4 libsm-dev libtasn1-3-dev libx11-dev libxau-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxmu-dev libxmu-headers libxrandr-dev
  libxrender-dev libxt-dev mesa-common-dev qt3-dev-tools
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev zlib1g-dev
Suggested packages:
  libcairo2-doc libgcrypt11-doc libglib2.0-doc gnutls-doc gnutls-bin
  libgtk2.0-doc krb5-doc libpango1.0-doc imagemagick libqt3-mt-psql
  libqt3-mt-mysql libqt3-mt-odbc libqt3-i18n qt3-doc alien mailx
Recommended packages:
  libqt3-compat-headers
The following NEW packages will be installed:
  comerr-dev kernel-wedge libatk1.0-dev libaudio-dev libbeecrypt6
  libcairo2-dev libcupsys2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglib2.0-dev
  libglu1-mesa-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev libgtk2.0-dev
  libice-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev liblzo2-dev
  libmng-dev libneon25 libopencdk8-dev libpango1.0-dev libpng12-dev
  libpopt-dev libqt3-headers libqt3-mt libqt3-mt-dev librpm4 libsm-dev
  libtasn1-3-dev libx11-dev libxau-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev
  libxt-dev libxtst-dev libxxf86misc-dev libxxf86vm-dev mesa-common-dev
  qt3-dev-tools rpm sharutils x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev zlib1g-dev
0 upgraded, 74 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.3MB/26.6MB of archives.
After unpacking 84.6MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  x11proto-core-dev libice-dev libsm-dev libxau-dev libxdmcp-dev
  x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev
  x11proto-fixes-dev libxfixes-dev x11proto-composite-dev libxcomposite-dev
  x11proto-render-dev libxrender-dev libxcursor-dev x11proto-damage-dev
  libxdamage-dev libxext-dev libexpat1-dev zlib1g-dev libfreetype6-dev
  libfontconfig1-dev libxft-dev libxi-dev x11proto-xinerama-dev
  libxinerama-dev libxmu-headers x11proto-randr-dev libxrandr-dev libxt-dev
  x11proto-record-dev libxtst-dev x11proto-xf86misc-dev libxxf86misc-dev
  x11proto-xf86vidmode-dev libxxf86vm-dev kernel-wedge libglib2.0-dev
  libatk1.0-dev libbeecrypt6 libpng12-dev libcairo2-dev libgnutlsxx13
  libgpg-error-dev libgcrypt11-dev libtasn1-3-dev libpopt-dev libopencdk8-dev
  liblzo2-dev libgnutls-dev libkadm55 comerr-dev libkrb5-dev libcupsys2-dev
  mesa-common-dev libgl1-mesa-dev libglu1-mesa-dev libpango1.0-dev
  libgtk2.0-dev libjpeg62-dev liblcms1-dev libmng-dev libneon25 libqt3-headers
  libqt3-mt libxmu-dev libaudio-dev qt3-dev-tools libqt3-mt-dev librpm4 rpm
  sharutils
E: There are problems and -y was used without --force-yes
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev
----- end log -----

I have no idea what that means!  I didn't give any -y or --force-yes (I was using a GUI) so I don't know what that's about.  Nor do I know why it can't install those packages.

Before I was just annoyed, but now I'm angry.  I may have wasted $50 on a video card I don't need.  Is there anything I can do to salvage this mess other than switch back to the old card?

---

### Post by llamakc on 2008-01-09
sudo apt-get install nvidia-settings

---

### Post by beachedwhale on 2008-01-09
I also tried the reconfigure thing. Identical results as the old card.

I also tried the Screens and Graphics utility again.  If I make any change and press Test, the dialog just disappears!  (And no change is actually made either.)

---

### Post by beachedwhale on 2008-01-09
> **llamakc said:**
> sudo apt-get install nvidia-settings

Thanks, that command completed successfully.  What next though?  I tried Screens and Graphics again.  This time instead of just exiting, it shows me one giant grey screen with nothing else on it, which I'm pretty sure is bad, so I tell it not to keep that configuration.  I also tried envy again but with the same error.

---

### Post by beachedwhale on 2008-01-09
I tried reconfigure again after that last install nvidia-settings command, and holy carp!  Reconfigure actually worked!  You are awesome!  Thanks.

---

### Post by beachedwhale on 2008-01-09
I may have spoken too soon, although I am further along than before.  What would this mean?

$ nvidia-settings -g

ERROR: NV-CONTROL extension not found on this Display.

ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.

ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

Also, the graphics are unusually slow, the speed I'd expect Windows "safe mode" to operate at.

I tried to run Second Life (to test the graphics), and it immediately gives me an error about needing OpenGL drivers and 32 bit graphics.  How do I do that?  It doesn't appear to let me set it over 24 bit in the auto config, and I'm not sure how to get OpenGL working without breaking what I already did.

---

### Post by beachedwhale on 2008-01-09
Should I be using nvidia-glx instead of nvidia-settings?  I'd try it but not if its going to mess things up.  Something's still not right here.  I can't believe graphics would be this slow on a properly configured computer with a fast video card and P4 2.8GHz.  Full screen video operates at a rate of about 1 frame every 3 seconds.

---

### Post by Fizz.LeChat on 2008-01-10
> **beachedwhale said:**
> Should I be using nvidia-glx instead of nvidia-settings?  I'd try it but not if its going to mess things up.  Something's still not right here.  I can't believe graphics would be this slow on a properly configured computer with a fast video card and P4 2.8GHz.  Full screen video operates at a rate of about 1 frame every 3 seconds.

Just a word from a noob, I'm now using a GeForce 6200 256MB AGP on my Sempron 2800 1GB with an ACER 22" LCD and it runs the advanced Desktop effects (Compiz)  including the spinning cube with 5 open desktops and all running firefox with videos etc.... I opted for the 6200 for reliability and cost. I love this card! I LOVE my desktop now!!!   :biggrin:

My 70yr old mom asked me to install Ubuntu 7.10 on her PC (it works great on her laptop). XP kept crashing/freezing on the PC ever since new and after 4 trips back to the shop she's had enough! I discovered it turns out the ATI card was the problem. I installed the Geforce 6200 and all is fine!

I'm also setting up another PC for my sisterwith Ubuntu 7.10 and suggesting she ditch the ATI card since I can't get more than basic graphics also... Not worth the time and trouble! Go NVidia!!!

I didn't make a note of every step... I will next time so I can help others... This is what worked for me after a few tries...

In the APPLICATIONS "ADD/REMOVE" Select (at top right)  ALL available applications
then Search: NVidia

I have checked "Restricted Drivers"
I also have checked the "NVidia binary X.Org driver ("new" driver)"
then "INSTALL"

Once installed and updated, Go to "System" - "Administration" - "Screen and Graphics"
graphics card setting = (NVidia GeForce 6800 (generic))
screen setting = Custom 1 *******<for me because of 22" LCD!>
resolution = 1680 x 1050

WARNING!!!! If you don't know how to command line to restore your settings go easy when selecting the resolution, choose progressively or you may not be able to go back... Been there, done that... I wasted a lot of time! 

Hope this helps someone else!

Fizz LeChat.... 
I'm the guy who hates command lines because he gets easily confused just entering username and passwords...  ](*,)

GeForce 6200 256MB AGP(50$) 
ACER 22" LCD (260$)
 in Quebec, Canada

---

### Post by beachedwhale on 2008-01-11
OK, I just tried that. I had to remove nvidia-settings package first.  It "worked" except that everything is identical to before, even after a reboot.  How do I tell its working?  What's a good Linux 3D graphics app that'd show off its stuff?

---

### Post by beachedwhale on 2008-01-11
Its not working.  Horridly slow or spews errors.

I have no idea what apps are good to try on Linux, so I downloaded something called Alien Arena.  It just does this:

~$ alien-arena
using /home/chuck/.alien-arena/data1/ for writing
using /home/chuck/.alien-arena/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 22050
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual, Stencil Buffered
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual
ref_gl::R_SetMode() - invalid mode
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual, Stencil Buffered
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual
ref_gl::R_SetMode() - could not revert to safe mode
ref_gl::R_Init() - could not R_SetMode()
recursive shutdown
Error: Couldn't initialize renderer!


Looks like the graphics are still messed up!  Any ideas on how to solve?

I tried Second Life again also, and no luck.

---

### Post by beachedwhale on 2008-01-11
And here's another that won't work:

~$ dreamchess
DreamChess v0.1.0 (r430)
Video mode set failed: Couldn't find matching GLX visual


SOMETHING is wrong here but I have no idea how to solve it.  I've done everything that I've read on what to do.  So far, 0 apps work that rely on accelerated graphics.

---


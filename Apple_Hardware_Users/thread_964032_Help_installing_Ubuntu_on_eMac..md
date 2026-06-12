---
title: "Help installing Ubuntu on eMac."
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by apa240 on 2008-10-30
I've burned the iso and started up the computer from the cd fine. It gets through the startup screen, with the bar sliding back and forth, but then just goes to a blank screen from there. Any ideas?

---

### Post by tiresia on 2008-10-30
Try to type at yaboot prompt```
video=ofonly
```

---

### Post by apa240 on 2008-10-30
I typed that in and got a response of:
video=ofonly:2,/vmlinux: Unable to open file, Invalid device

I've also tried booting up with "live video=ofonly" and have gotten nowhere with that.

---

### Post by tiresia on 2008-10-30
Where did you download the CD, and how did you burn it? Please, give us more informations about your computer

---

### Post by apa240 on 2008-10-30
I got it from [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/) and burned it using Disk Utility. (I realize that's 8.04, but I did it earlier this week.)

eMac
1.42 GHz PPC G4
1 GB RAM
ATI Radeon 9600
Combo Drive

I don't know what else you need.

---

### Post by tiresia on 2008-10-30
If you downloaded a LiveCD, at the yaboot-prompt type```
live-nosplash-powerpc video=ofonly
```Burn the CD very slowly
You will get help from other people who know better the eMac
You may find more in this forum. A similar problem:
[http://ubuntuforums.org/showthread.php?t=795795&highlight=emac](http://ubuntuforums.org/showthread.php?t=795795&highlight=emac)

---

### Post by crapple on 2008-10-30
Try this.

1) Download alternative install cd.  Live ones don't do to well on ppc. Get it form [here]("http://cdimage.ubuntu.com/ports/releases/hardy/release/")

2) Install

3) If it works great! If you get a screen that flickers and then goes black try this.

4) Switch to terminal based interface(alt+F1 might take a few times.)

5)Run ```
wget http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.6.3-2_powerpc.deb
```
You must have a weird internet connection.
6)Run ```
sudo dpkg -i --force all xserver-xorg-video-ati_6.6.3-2_powerpc.deb
```
7)Run ```
sudo /etc/init.d/gdm restart
```
(8)Then if needed press alt+F7 to get to graphical interface.  This should make it run in low graphics.
9)Then open terminal (Applications-accessories-terminal)and run```
sudo gedit /etc/X11/xorg.conf
```
10)Select everything then paste this in
```
# xorg.conf (X.Org X Window System server configuration file)
#
# See the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.

Section "ServerLayout"
        Identifier      "XFree86 Configured"
        Screen          0 "Screen0" 0 0
        InputDevice     "Mouse0" "CorePointer"
        InputDevice     "Keyboard0" "CoreKeyboard"
        Option          "OffTime" "10"
EndSection

Section "Files"
# RgbPath is the location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)

       RgbPath		"/usr/share/X11/rgb.txt"
      #FontPath		"/usr/share/X11/fonts/misc:unscaled"
      #FontPath		"/usr/share/X11/fonts/Type1/"
      #FontPath		"/usr/share/X11/fonts/Speedo/"
      #FontPath		"/usr/share/X11/fonts/75dpi:unscaled"
      #FontPath		"/usr/share/X11/fonts/100dpi:unscaled"
EndSection

Section "Module"
        Load            "dbe"
        Load            "extmod"
        Load            "fbdevhw"
        Load            "freetype"
        Load            "type1"
        #Load           "dri"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
# Change "XkbModel" to "macintosh_old" if you are using
# the deprecated adb keycodes.
        Option          "XkbModel"      "macintosh"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "grp:caps_toggle"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "ZAxisMapping"  "4 5"
        Option          "Protocol"      "IMPS/2"
        Option          "Device"        "/dev/input/mice"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        ModelName       "Monitor Model"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-60
EndSection

Section "Device"
        Identifier      "Card0"
        #Option         "ShadowFB"      "true"
        #Option         "fbdev"         "/dev/fb0"
        Driver          "fbdev"
        #BusID          "PCI:0:16:0"
        Option          "UseFBDev"      "true"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes   "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Group           0
        Mode            0666
EndSection
```

I got this for my emac from paul_mcl.

Then run update manger from system-administration.

This worked for me on my Radeon 7500 emac g4. 

Good Luck!

---

### Post by apa240 on 2008-11-01
I got it to work. I typed in the code for the xorg.conf that crapple said and got it to load with the live cd.

Thanks for your help tiresia and crapple.

---

### Post by kububa on 2008-11-05
Wonderful!!!!! Thank you for solution!!! 
I was struggling with this problem for quite a long time and I could only install on my 1.2 GHz eMac with ati card Ubuntu 6.06, all newer versions failed - black screen.

So now I have Ubuntu 8.04.1 on my eMac, but I've noticed my soundcard is not working. Is it working on your eMacs, guys?

---

### Post by stream303 on 2008-11-09
If you call up **alsamixer** in a terminal, are any of your outputs muted, or sitting at very low levels?  (left-right keys to navigate, M to toggle muting, B to balance, up-down to change levels..)

PulseAudio might be suspect too, but I'd check alsamixer first...

Typically I've found PCM to be blasting on ppc installs, but perhaps not on your emac....

---

### Post by crapple on 2008-11-09
I am glad it worked for you. I am posting a solution on how to get interpread to work with emacs. What you need is a hardy or earlier xorg file. Under driver for the graphics card instead of ati switch it to fbdev and it works like a charm except for desktop effects. 
Hope this helps if you want to try interpread

---

### Post by crapple on 2008-11-09
To get sound working you need to run
```
sudo modprobe snd-powermac
```

Then to get sound working automatically you need to do this
```
sudo nano -w /etc/modules
```
then add 
```
snd-powermac
```
to the list.  

Then restart and sound should work.

---

### Post by kububa on 2008-11-10
Thank you Crapple. Now I have sound working on my emac too in Ubuntu 8.04.1.
By the way, ```
sudo modprobe snd-powermac
``` did not work on Ubuntu 8.10, there was no sound, but 8.04.1 is fine so far.

---

### Post by crapple on 2008-11-11
It works in interpid after you add it to the modules list and restart.

---

### Post by kububa on 2008-11-12
Yes, Crapple, I confirm, sound is working on Interpid as well. Thanks!

Another question: on Interpid my eMac box works only with fbdev driver, it's fine for me as I do not need 3d acceleration, but I do not know how to change resolution. It seems to me that changing xorg.conf is not effecting on the system. To change the resolution I calculated Modeline on this page [http://www.arachnoid.com/modelines/]("http://www.arachnoid.com/modelines/") and pasted it to xorg.conf.
```
Modeline "1152x864_80.00" 112.36 1152 1224 1352 1552 864 865 868 905 -HSync +Vsync
```
Then I added ```
Modes "1152x864" "1024x768"
``` in my Screen section of xorg. But nothing changed after restarting. I can not change resolution in gui either (System>Preferences>Resolution).
On Ubuntu 8.10 on my macmini with Intel processor I found the monitors' configuration file under /home/username/.config/monitors.xml.

Does anyone knows how to change resolution to 1152x864?

---

### Post by geopgeop on 2008-11-14
Kubaba, sudo apt-get install read-edid, then type

```
# sudo get-edid | parse-edid
```

This might help you write a working modeline for your particular eMac.

This is the output on my eMac 2005 Radeon 9600:

```

parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum passed.

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "iMac"
        VendorName "APP"
        ModelName "iMac"
        # Block type: 2:0 3:fd
        HorizSync 71-73
        VertRefresh 70-140
        # Max dot clock (video bandwidth) 130 MHz
        # Block type: 2:0 3:fc
        # DPMS capabilities: Active off:no  Suspend:no  Standby:no

        Mode    "1024x768"      # vfreq 88.995Hz, hfreq 72.086kHz
                DotClock        99.190000
                HTimings        1024 1072 1168 1376
                VTimings        768 769 772 810
                Flags   "+HSync" "+VSync"
        EndMode
        Mode    "1280x960"      # vfreq 71.932Hz, hfreq 72.075kHz
                DotClock        122.240000
                HTimings        1280 1328 1424 1696
                VTimings        960 961 964 1002
                Flags   "+HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
EndSection

```

Then again, I don't see 1152x864 from this output...

Just to know, I got this info from an old post here: [http://ubuntuforums.org/showpost.php?p=1476073&postcount=13](http://ubuntuforums.org/showpost.php?p=1476073&postcount=13)

Also,

I wish I could upgrade my eMac past Feisty, but I really don't want to force old drivers or use fbdev. Is there an xserver-xorg-video-radeon on Intrepid or later that actually works with my eMac? I'm using the built-in CRT - not any external monitors, if that helps.

---

### Post by kububa on 2008-11-18
geopgeop, thanks for your tip. However, it's interesting that sudo get-edid | parse-edid is not showing 1152x864 resolution, as I can choose this resolution in Mac OS on my eMac.
Another thing is, changing resolution in xorg is not affecting computer when using fbdev driver.
I'm also looking forward to working ati driver again for my eMac, but it probably this time will never come... :-( Or maybe?
There is a bug described here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/93509]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/93509")

---

### Post by kerryhall on 2008-12-18
Is it possible to get hardware OpenGL acceleration on an eMac?

---

### Post by kerryhall on 2008-12-18
> **crapple said:**
> Try this.
Good Luck!

Yo, Crapple, that worked like a charm!! I tried running glxgears, and I got something like 220 fps, but it looked choppy.

Is there anyway to get non-choppy OpenGL going on my machine? (It's identical to yours I believe)

Thanks!

---

### Post by Kanji_Man on 2008-12-29
Thanks to this and other threads I was recently able to install intrepid ibex on my eMac 1.25Ghz (USB 2.0). Here is the overall process:

- Boot the [ubuntu-8.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/intrepid/release/ubuntu-8.10-alternate-powerpc.iso)
- When you get the text menu for language selection press CTRL+ALT+F2 for a secondary text console.
- At the busybox prompt enter "modprobe ide-scsi" to wake up your optical drive so that it can be detected.
- Type "exit" and then CTRL+ALT+F1 to return to the installation

- Complete the text-mode installation process for Ubuntu.

- When the system reboots wait to get past the bootstrap, yaboot and the splash screens. Then the screen will flicker and go blank.
- Press CTRL+ALT+F1 for a text console.
- Login with the account you created during the ubuntu installation.
- Enable sound by using the command "sudo nano /etc/modules", add the line "snd-powermac" (without quotes), then CTRL+X to exit and save.
[s]- You can install the ati xserver with the command "sudo apt-get install xserver-xorg-video-ati"
- Use the command "sudo nano /etc/X11/xorg.conf" to edit the X configuration. The default intrepid configuration is empty as it tries to autodetect everything. Replace it with this (easier to copy from a mounted flash drive):
- Again use CTRL+X to exit, then save.[/s]
[center]** SEE UPDATED INFORMATION ON NEXT POST **[/center]

- Use the command "sudo shutdown -r now" to reboot the system and you should now have an eMac running a basic install of Intrepid Ibex with functioning sound and a decent resolution.

[s]-I have not been able to enable desktop effects (aka compizfusion) however you can enable basic compositing under metacity with this command:
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true[/s]

---

### Post by Kanji_Man on 2009-01-04
After much experientation, digging around the internet and sifting through mountains of forum posts both here and elsewhere, I have found the magic line that will allow my eMac to use the default xserver with default ati driver using the internal display under intrepid. Under the "Device" section for your video card, you need to add the option "monitor-DVI-0" and point it to the name you gave for the monitor. My revised */etc/X11/xorg.conf* file:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# See the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.

Section "ServerLayout"
	Identifier	"eMac Configuration"
	Screen 0	"Screen0"		0 0
	InputDevice	"Apple Mouse"		"CorePointer"
	InputDevice	"Apple Keyboard"	"CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier	"Apple Keyboard"
	Driver		"kbd"
	Option		"XkbModel"		"macintosh"
	Option		"XkbLayout"		"us"
	Option		"XkbOptions"		"grp:caps_toggle"
EndSection

Section "InputDevice"
	Identifier	"Apple Mouse"
	Driver		"mouse"
	Option		"ZAxisMapping"		"4 5"
	Option		"Protocol"		"IMPS/2"
	Option		"Device"		"/dev/input/mice"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	71-73
	VertRefresh	70-140
	Modeline	"1024x768" 99.190000 1024 1072 1168 1376 768 769 772 810 +HSync +VSync
	Modeline	"1280x960" 122.240000 1280 1328 1424 1696 960 961 964 1002 +HSync +VSync
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200]"
	BusID		"PCI:0:16:0"
	Driver		"ati"
	Option		"monitor-DVI-0"		"iMac"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies Inc RV280 [Radeon 9200]"
	Monitor		"iMac"
	DefaultDepth    24
	SubSection "Display"
		Depth   24
		Modes   "1280x960" "1024x768" "800x600"
	EndSubSection
EndSection
```
This is tested as working with a default install of intrepid ibex on an eMac 1.25Ghz (USB 2.0) with onboard ATI Radeon 9200. [s]I still have not been able to enable desktop effects but I think this is a significant step in the right direction.[/s]

EDIT: The reason I was unable to enable desktop effects was because I had enabled Compositing on metacity. Because of this, Compiz was unable to become the Compositng manager. After disabling compositing in metacity and rebooting, I was able to enable Advanced Desktop Effects.  I now have an eMac running Intrepid using the "ati" driver and have flipping cubes and everything on the internal display. Bluetooth and Airport Extreme modules are also working.

---

### Post by stream303 on 2009-01-05
Nice report!

You may have just solved quite a few problems for owners of more than just the emac.  I think there are quite a few just running fbdev instead of ati so this might be just the ticket.  Nice catch.

---

### Post by kububa on 2009-01-06
:D It works great on Hardy as well!
My wife is saying thank you, as I configured old eMac for her.
Till now she had to use fbdev driver.

Thanks!!!!! Good work!

---

### Post by julian265 on 2009-01-28
On my emac 700 - using snippets from other peoples xorg.conf files did not work.

I read the xorg documentation online, and was able to get it to make it's own xorg.conf file, then adjusted a few settings to get the desired resolution. (needed to make a modeline, and adjust the available modes)

This one really helped:
[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)

and also:
[http://www.freebsd.org/cgi/man.cgi?query=xorgcfg&sektion=1&manpath=X11R7.2](http://www.freebsd.org/cgi/man.cgi?query=xorgcfg&sektion=1&manpath=X11R7.2)

---

### Post by ant2ne on 2009-02-08
Using Kanji_Man's xorg.conf, I got my system to boot, but I don't think it is optimal. I can log in, but everything seems sluggish. Particularly anything graphics hungry, like playing avi files. I think that I need to fine tune my xorg.conf.

```
ant2ne@emac-ubuntu:/etc/X11$ lspci | grep VGA
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

```This shows that Kanji_Man and I have different VGA devices. But it was my understanding the Identifier section is for user identification, not the computers.

top doesn't show any process using more than 15% of CPU time. In fact it looks quite normal.
free shows it could defiantly use more RAM but it doesn't appear to be using all of its swap.

This defiantly has the feel of a system trying to display graphics that it is incapable of.

So any hints on to what I should be changing in the xorg.conf? Or any other ideas why this system is so sluggish.

---

### Post by kububa on 2009-07-16
Hi ant2ne,
Here are some clues how to check whether everything is installed ok.

I ASSUME you followed the instructions in this post.
What comes to my head:

1. Check, whether radeon driver is loaded. Type:

```
lsmod
```

2. Try also glxgears whether it works.
```
glxgears -fullscreen
```
I get around 78 frames in 1152x864 resolution.

3. I installed xfce instead of gnome, it's a little bit faster.
4. I use resolution 1152x864 - it's a little bit faster than the 1280x960.
5. How much RAM do you have? For Gnome 500 MB is ok, for xfce less is fine.
6. Firefox works really slow, when there are a lot of flash animations, but there is no help for this.

Hope this helps.

---

### Post by ant2ne on 2009-07-16
Thanks for the reply. I fixed this issue by upgrading my ram. I had 126 which simply isn't enough. I put in another 126 stick and the system responded better. But, i wanted to run XBMC and view adobe flash based sites (hulu) on this box, so I was forced to re-install OS X. The XBMC runs great on OS X. I'm still running ubuntu on my iBook though.  ;-)

---

### Post by sir_cheats_a_lot on 2010-01-06
awesome.  thanks a bunch for that.  now i just need to get NWN running on my eMac. got the full rendering it looks like.  even compiz is working. \\:D/

---

### Post by oswaldkelso on 2010-01-06
```
#pragmarts emac 1ghz ATI Debian lenny xorg.conf
#pragmarts emac xorg.conf
#ref: Spanish: http://putolinux.wordpress.com/2008/09/06/xorgconf-para-un-****-emac-1280x960/
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
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/X11R6/lib/X11/fonts/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/X11R6/lib/X11/fonts/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/X11R6/lib/X11/fonts/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/X11R6/lib/X11/fonts/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    FontPath    "/usr/X11R6/lib/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
    Load    "dbe"
    Load    "type1"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
#    Option         "XkbLayout"     "gb" #British
#    Option        "XkbLayout"    "es" #spanish
    Option        "XkbLayout"    "us" #USA
    Option        "XkbOptions"    "lv3:lwin_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
    Driver        "radeon"
    BusID         "PCI:0:16:0"
    Option        "monitor-DVI-0"        "Monitor[0]"
EndSection

Section "Monitor"
  DisplaySize  320 240
  HorizSync    71.0-73.0
  Identifier   "Monitor[0]"
  ModelName    "APPLE EMAC"
  Option       "DPMS"
  Option       "PreferredMode" "1280x960"
  VendorName   "APP"
  VertRefresh  70-140
  UseModes     "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
  Modeline     "1280x960" 122.2 1280 1334 1448 1696 960 961 964 1002 +hsync +vsync -csync
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "DRI"
    Mode    0666
EndSection 
```

---

### Post by linuxopjemac on 2010-01-07
Oswald, can you check if we have this xorg.conf file in our website? I think it's the Radeon emac one, right?

---

### Post by HappinessNow on 2010-04-11
> **crapple said:**
> Try this.

1) Download alternative install cd.  Live ones don't do to well on ppc. Get it form [here]("http://cdimage.ubuntu.com/ports/releases/hardy/release/")

2) Install

3) If it works great! If you get a screen that flickers and then goes black try this.

4) Switch to terminal based interface(alt+F1 might take a few times.)

5)Run ```
wget http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.6.3-2_powerpc.deb
```
You must have a weird internet connection.
6)Run ```
sudo dpkg -i --force all xserver-xorg-video-ati_6.6.3-2_powerpc.deb
```
7)Run ```
sudo /etc/init.d/gdm restart
```
(8)Then if needed press alt+F7 to get to graphical interface.  This should make it run in low graphics.
9)Then open terminal (Applications-accessories-terminal)and run```
sudo gedit /etc/X11/xorg.conf
```
10)Select everything then paste this in
```
# xorg.conf (X.Org X Window System server configuration file)
#
# See the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.

Section "ServerLayout"
        Identifier      "XFree86 Configured"
        Screen          0 "Screen0" 0 0
        InputDevice     "Mouse0" "CorePointer"
        InputDevice     "Keyboard0" "CoreKeyboard"
        Option          "OffTime" "10"
EndSection

Section "Files"
# RgbPath is the location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)

       RgbPath		"/usr/share/X11/rgb.txt"
      #FontPath		"/usr/share/X11/fonts/misc:unscaled"
      #FontPath		"/usr/share/X11/fonts/Type1/"
      #FontPath		"/usr/share/X11/fonts/Speedo/"
      #FontPath		"/usr/share/X11/fonts/75dpi:unscaled"
      #FontPath		"/usr/share/X11/fonts/100dpi:unscaled"
EndSection

Section "Module"
        Load            "dbe"
        Load            "extmod"
        Load            "fbdevhw"
        Load            "freetype"
        Load            "type1"
        #Load           "dri"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
# Change "XkbModel" to "macintosh_old" if you are using
# the deprecated adb keycodes.
        Option          "XkbModel"      "macintosh"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "grp:caps_toggle"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "ZAxisMapping"  "4 5"
        Option          "Protocol"      "IMPS/2"
        Option          "Device"        "/dev/input/mice"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        ModelName       "Monitor Model"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-60
EndSection

Section "Device"
        Identifier      "Card0"
        #Option         "ShadowFB"      "true"
        #Option         "fbdev"         "/dev/fb0"
        Driver          "fbdev"
        #BusID          "PCI:0:16:0"
        Option          "UseFBDev"      "true"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes   "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Group           0
        Mode            0666
EndSection
```

I got this for my emac from paul_mcl.

Then run update manger from system-administration.

This worked for me on my Radeon 7500 emac g4. 

Good Luck!okay a few things

1. alternate cd would not work for me so using live cd

2. up to step 5 ran smoothly

3. step 6 did not run I got this message:

dpkg: error processing xserver-xorg-video-ati_6.6.3.2_powerpc.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
 xserver-xorg-video-ati_6.6.3.2_powerpc.deb


I then tried sudo gedit /etc/X11/xorg.conf

and I get this:

(gedit:3571): Gtk-WARNING **: cannot open display

4. how do I select everything and paste it in?

Please help

---

### Post by linuxopjemac on 2010-04-11
3. you didn't download the file. Do you have internet connection ?

4. You don;t have X, so you can't use gedit. Use nano instead:

```
sudo nano /etc/X11/xorg.conf
```

edit your file to your needs.
CTRL-X to exit and "y" to save.

Then you can try again to enter X:

```
sudo /etc/init.d/gdm restart
```

---

### Post by Kanji_Man on 2011-01-12
For what it's worth, I recently loaded Maverick 10.10 from [here]("http://cdimage.ubuntu.com/ports/releases/10.10/release/") and was able to boot the live cd on my eMac G4. I was able to install and pretty much everything worked out of the box.  I had to install the propietary driver for the wifi but the standard wizard made this easy.  The only tricky bit was the bluetooth module but I was able to correct this with "sudo apt get install blueman".

I have no /etc/X11/xorg.conf and I have the internal display working.

---

### Post by KingYaba on 2012-04-09
> **Kanj]
This is tested as working with a default install of intrepid ibex on an eMac 1.25Ghz (USB 2.0) with onboard ATI Radeon 9200.[/QUOTE]

I want to thank you for posting that xorg configuration. I have that exact eMac model and now I can use the 1280x960 resolution without any flickering or stuttering. Currently running 12.04. :guitar:

[QUOTE=Kanji_Man said:**
> For what it's worth, I recently loaded Maverick 10.10 from [here]("http://cdimage.ubuntu.com/ports/releases/10.10/release/") and was able to boot the live cd on my eMac G4. I was able to install and pretty much everything worked out of the box.  I had to install the propietary driver for the wifi but the standard wizard made this easy.  The only tricky bit was the bluetooth module but I was able to correct this with "sudo apt get install blueman".

No, booting into a live session wasn't an issue on my end either. The only thing I had to do was remove my optical drive from the eMac and replace it with a working one. My old drive kept giving I/O errors when booting from a disc.

---

### Post by sahdavies on 2012-09-18
I currently have 10.10 running on my Emac fine, install was a breeze......

However, trying to update to 11.04 causes the ATI card to blank out.....

The problem is apparently that there are 3 or 4 different Emacs some with ATI cards some without.

Stick with 10.10 and you'll be fine !

(side note, anyone got any ideas how to get flash working ! lol)


/. 2 things in life you can count on - (1) Nobody will tell you what the second one is

---

### Post by c4c on 2012-09-19
After setting up a few of the 1st gen eMacs with Lucid and lots of help from posters on this forum, I finally got the "Documents" section of our website done and there are a couple of pages that may be helpful.

[This page]("http://computers4christians.org/Document/Computer/Apple/PowerPC/eMac700.html") describes the "fix" for the CD tray (afraid you'll have to scroll to the bottom to see it).

[This page]("http://computers4christians.org/Document/HowTo/Flash.html") has several tips for flash (more accurately gnash, swfdec, flash-aid and vdh) that can be used in combination on PowerPCs.;)

---

### Post by sir_cheats_a_lot on 2012-09-20
> **sahdavies said:**
> I currently have 10.10 running on my Emac fine, install was a breeze......

However, trying to update to 11.04 causes the ATI card to blank out.....

The problem is apparently that there are 3 or 4 different Emacs some with ATI cards some without.

Stick with 10.10 and you'll be fine !

(side note, anyone got any ideas how to get flash working ! lol)



If you insist on installing it on a PPC Mac, I'd just do a clean install of Precise(12.04) if I were you.  It installs fine, and everything seems to work fine out of the box...except flash of course.   none of the alternatives seem to actually get flash media working.  I sat for 2 hours waiting for the players to load, which never happened.  genuinely if you want to view flash media, you're infinitely better off just sticking to OS X.  gnash(when it does load) is so choppy(or was, the current version isn't even working as far as I know) it makes watching videos painful, and not really even worth while.   swfdec is strictly a shockwave player, which worked little better then gnash did back in the 10.04 days.  there was another alternative, but it's based on more or less the same code as gnash, and works little better.
  there's really little point in having linux installed on the PPC platform, as in reality, you end up losing functionality.  it's fine if you only want to check email, and nothing else.  It's really not capable of doing anything else, because developers choose not to invest the resources for improving the platform.  as it is there's no way to play mac games on a ppc linux, or play flash videos.  Don't get me wrong, it works really well for what it can actually do, but the only real advantage is the possibility of security updates(which OS X 10.4 and 10.5 lacks).  Now...if VideoLan decided to make a working browser plugin, and a way to use it directly within the browser, you could probably watch flash video with no troubles.  also...mind your partition scheme, once you set it at install there's literally no way to change it without reinstalling absolutely everything.

---


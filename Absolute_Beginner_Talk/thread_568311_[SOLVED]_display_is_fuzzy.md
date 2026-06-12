---
title: "[SOLVED] display is fuzzy"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by K5KS on 2007-10-05
successfully Installed Ubuntu 7.04 on Gateway Solo 2500.  everything is working for the most part.
One Issue:  800x600 is the max resolution for the display. (it can be higher with an external monitor).  The fonts are very fuzzy.  I paged through several post and did not see what I should do.   

Is there a particular setting that I am missing.

---

### Post by kellemes on 2007-10-05
Based on your videocard try to find out what driver to install to get the most out of it.

---

### Post by K5KS on 2007-10-05
how do I figure out what card is in the system.  New to Ubuntu where is the systems info located

---

### Post by Jimmyfj on 2007-10-05
In System>Administration>Restricted Drivers Manager you will be able to see what driver Ubuntu will install on your system. Just tick the driver shown and then click Enable Driver. Then reboot your computer when asked to do so.

---

### Post by K5KS on 2007-10-05
When I did that I got this message:  my hardware does not require any restricted drivers.

Keep in mind that is a very old laptop. It still works as I am on now.  If I could only fix the font all would be great.

any other ideas?

Info about the card?  any idea on drivers...next question will be how to install
Neomagic Corporation NM2160 [MagicGraph 128XD

---

### Post by mgmiller on 2007-10-05
If it's just fuzzy fonts that bother you, try System > Preferences > Font and try different fonts.  My favorite is DejaVu Sans Condensed.  
Try different sizes for the fonts as well as sometimes a font looks great at one point size and crummy at another.

Also, on this same window look at the Font Rendering area and try checking Subpixel Smoothing (LCD's).  This makes a big difference on LCD screens.

Between these 2 items, you should get a pretty good looking display.

Good Luck

Edit:  I just had a look at your specs and if you have the 12.1 inch screen, then 800x600 is your native resolution.  Don't try to go higher if this is the case or your display will go "out of range" and appear black.
If you have the 13.3 inch screen, then your native resolution is 1024x768 and trying to get the higher resolution might be helpful.  

Here is what I found out about your video card:
NeoMagic NM2160 High Performance Multimedia Flat Panel/CRT GUI Accelerator with 2 MB integrated RAM; Interface: 32-bit burst mode PCI bus with 128-bit memory interface
External video: Supports simultaneous LCD/External monitor; variable sync for compatibility with a wide range of monitors

In any case, try fixing the fonts as I suggested above and see how you like it.

---

### Post by EnigmaX on 2007-10-05
I had the same issue on my install of 7.0.4.  I'm using an ATI video card, display was set to 1280x1024, I used the information in the sticky of this forum to use the ATI video drivers.  My display (system, browser, etc) is crystal clear now.

Not sure if that is helpful at all...

---

### Post by n3tfury on 2007-10-05
> **mgmiller said:**
> If it's just fuzzy fonts that bother you, try System > Preferences > Font and try different fonts.  My favorite is DejaVu Sans Condensed.  
Try different sizes for the fonts as well as sometimes a font looks great at one point size and crummy at another.

Also, on this same window look at the Font Rendering area and try checking Subpixel Smoothing (LCD's).  This makes a big difference on LCD screens.

Between these 2 items, you should get a pretty good looking display.

Good Luck

Edit:  I just had a look at your specs and if you have the 12.1 inch screen, then 800x600 is your native resolution.  Don't try to go higher if this is the case or your display will go "out of range" and appear black.
If you have the 13.3 inch screen, then your native resolution is 1024x768 and trying to get the higher resolution might be helpful.  

Here is what I found out about your video card:
NeoMagic NM2160 High Performance Multimedia Flat Panel/CRT GUI Accelerator with 2 MB integrated RAM; Interface: 32-bit burst mode PCI bus with 128-bit memory interface
External video: Supports simultaneous LCD/External monitor; variable sync for compatibility with a wide range of monitors

In any case, try fixing the fonts as I suggested above and see how you like it.

the biggest difference for me was installing the gutsy beta.  i'm not sure what they've done, but it looks the sharpest of any distro i've tried to date.  and i've not applied anything other than what came set as default.  i have an nvidia 6200.

---

### Post by K5KS on 2007-10-09
I did try working with the Font (had done this prior but thought I would give another shot) nothing improved.  I have done some more homework about the Neomagic Video card that is installed.  I am trying to find out more about the XFree86 driver...see below.

Installed Ubuntu on Gataway 2500 Solo PII 233. Everything works well except the display is very fuzzy(fonts graphics...everything). I have read many post on Drivers/ and video cards and all of those containing Neomagic etc...

The Laptop TFT  supports up to 800x600 which is ok if it was not so fuzzy. I have read post about the XFree86 driver for this chip set.

1. how do I know if I have that driver
2. how do I get/install if I don't
3. is there more detailed setting that I need to adjust to clear up the fuzzy display.

:confused:

---

### Post by mgmiller on 2007-10-10
> 1. how do I know if I have that driver

In a terminal type:
```
cat /etc/X11/xorg.conf
```

Scroll down to the section headed    Section: " Device"

It will have a line telling you what video card and what driver.
For example, mine says ...
Identifier  "Generic Video Card"
Driver      "nvidia"

The above command is a safe, "read only" thing.
If you are going to attempt to make changes by any method,
before doing anything to this file, you should make a backup of it, just in case:
```
sudo cp /etc/X11/xorg.conf xorg.backup
```

> 2. how do I get/install if I don't
3. is there more detailed setting that I need to adjust to clear up the fuzzy display.

I only have experience with nvidia and ati video cards/drivers, so I can't comment on which driver is appropriate for your neomagic card.  I do know there are a lot of drivers that are "built in" to the distribution and can be selected by editing the xorg.conf file and just typing in the one you want to load on the Driver line.

You may also be able to run the following in a terminal to tell the system exactly which driver to use:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

You can accept the defaults for the things you don't know.  When you get to the driver part, there should be a list of available drivers, just select the one you want.  

The only other thing I can think of is did you try adjusting the brightness and contrast settings on the monitor?  A too bright display can sometimes appear "fuzzy".

Good Luck.

---

### Post by K5KS on 2007-10-10
So I did reconfigure the xserver  and ensured that the neomagic driver was selected.  I also removed the 1280x1024 option as my display does not support that.  is there anything specific that I need to do after that.  I did restart the laptop but noticed no difference in the screen/fuzzy display.  

The xorg.conf shows the modified settings by only showing the 800x600 in the display.  Also the dirver is and was listed as the neomagic.  In reading the note below is there any edit that should be made to remove the display depths that are not 8 and 16 respective.  I included a link to the xorg.conf file this person used on a gateway solo 2500 (same machine and video card)

the link came from this site: [http://www.thehayesweb.org/jhayes/solo2500.html](http://www.thehayesweb.org/jhayes/solo2500.html)
[INDENT]
Here is a note that I found on the web from someone(link abover) that installed RedHat 7.1 :
I use the neomagic driver with XFree86 4.1.0. The chipset is NeoMagic's NM2160 (MagicGraph 128XD) Using the NeoMagic driver, I get a resolution of 800x600 at pixel depths of 8 and 16 (Note that the chipset can actually handle higher resolutions and bit depths. I'm limited to 800x600, 16 bpp by the 2500's LCD). Here's a copy of my [XF86Config-4]("http://www.thehayesweb.org/jhayes/XF86Config-4") file  and my for the Solo 2500 (use at your own risk).[/INDENT]

One other note is that I did hook up to an external monitor and had the same fuzzy display.  Funny thing is that when I took a screen shot and emailed it to myself my other computers rendered the screen shot crystal clear.  I previously had Win 2000 on this machine and the display was clear so I know it can happen.  I am determined to get this right.

quick eidt: [http://linux.die.net/man/4/neomagic]("http://linux.die.net/man/4/neomagic")  info found at this link: 
Description
neomagic is an Xorg driver for the Neomagic graphics chipsets found in many laptop computers.
Supported Hardware
neomagic supports the following chipsets:

MagicGraph 128 (NM2070)
MagicGraph 128V (NM2090)
MagicGraph 128ZV (NM2093)
MagicGraph 128ZV+ (NM2097)
**_MagicGraph 128XD (NM2160)_** (my specific chipset)
MagicGraph 256AV (NM2200)
MagicGraph 256AV+ (NM2230)
MagicGraph 256ZX (NM2360)
MagicGraph 256XL+ (NM2380)

The driver supports depths 8, 15, 16 and 24 for all chipsets except the NM2070 which does not support depth 24. All depths are accelerated except for depth 24 which is only accelerated on NM2200 and newer models. All visuals are supported in depth 8. TrueColor and DirectColor visuals are supported in the other depths.
Configuration Details
Please refer to xorg.conf(5x) for general configuration details. This section only covers configuration details specific to this driver.

The following driver Options are supported

Option NoAccel boolean
    Disable or enable acceleration. Default: acceleration is enabled. 
Option SWCursor boolean
    Disable or enable software cursor. Default: software cursor is disable and a hardware cursor is used. 
Option PCIBurst boolean
    Disable or enable PCI burst modes. Default: enabled. 
Option Rotate CW
Option Rotate CCW
    Rotate the display clockwise or counterclockwise. This mode is unaccelerated. Default: no rotation. 
Option ShadowFB boolean
    Enable or disable use of the shadow framebuffer layer. Default: off. 
Option OverlayMem integer
    Reserve the given amount of memory (in bytes) for the XVideo overlay. On boards with limited memory, display of large XVideo buffers might fail due to insufficient available memory. Using this option solves the problem at the expense of reducing the memory available for other operations. For full-resolution DVDs, 829440 bytes (720x576x2) are necessary.

Note
On some laptops using the 2160 chipset (MagicGraph 128XD) the following options are needed to avoid a lock-up of the graphic engine:

Option "XaaNoScanlineImageWriteRect"
Option "XaaNoScanlineCPUToScreenColorExpandFill"

See Also
Xorg(1x), xorg.conf(5x), xorgconfig(1x), Xserver(1x), x(7)
Authors
Authors include: Jens Owen, Kevin E. Martin, and also Egbert Eich, Mark Vojkovich, Alan Hourihane.
REFERENCED BY 
xorg(1), xorg.conf(5)

---

### Post by mgmiller on 2007-10-10
Please post your xorg.conf file so I can take a look.  
Maybe I'll spot something you missed.

---

### Post by K5KS on 2007-10-10
Here it is. I did upgrade to 7.1 today as a matter of running out of things to try.  It did not seem to make a difference.  another thing I noticed is that as Ubuntu is booting up the Ubuntu graphic/logo is clear and sharp but once the OS loads and the desktop comes up everything is fuzzy.  it is crazy because everything else works.


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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "Generic Video Card"
        Driver          "neomagic"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-40
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "800x600" "640x480"
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
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by mgmiller on 2007-10-11
I really don't see any problems here.  Have you experimented with different color depths?

try changing this area:
```
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
```

So it reads DefaultDepth 16
You can also try 15 as it's in your mode lines.

After each change, you will need to restart x, so log off and do a ctrl alt backspace.

If that command no longer works in Gutsy, then just restart the computer.

Here are some extra commands that have been used by others with your video card   They are  added in the Section "module"

Section "module".
```
Load "type1"
Load "GLcore"
Load "dbe"
```

I would suggest adding them one at a time and see what happens.

Again, you will need to restart x after each change to see what effect it has.

Also, remember to make a backup of your current xorg.conf before starting so you can easily restore it if something goes bad.

---

### Post by K5KS on 2007-10-11
made back up of file  and made change to: 
DefaultDepth 15
and added 
Load "type1" to Module section

Result is a continuous cycle between the Loading Screen with spinning wheel and the black screen with last entry being 

* running local boot scripts (/etc/rc.local)

Need Help...something broke  the desktop never loads????

---

### Post by mgmiller on 2007-10-11
This is why you made the backup.  Can you change to a different terminal by typing ctrl alt F1?
You should get a black DOS like screen asking for a log in.  Give it your regular user name and password.  Then type the following code to copy your backup back where it belongs.  

For this example, I am assuming the name of the backup file is xorg.backup.   You should substitute whatever you named it.
```
sudo cp /etc/X11/xorg.backup xorg.conf
```

Give it your password when it asks and you can then go back to ctrl alt F7 and then hit ctrl alt backspace to restart x.

You should be back where you started.

By the way, you made 2 changes at once, so you don't know which one caused the problem.

---

### Post by K5KS on 2007-10-11
I will try this tonight.  The only problem is that I don't get to a desktop.  It never loads only going back and forth as I mentioned above.  Do I start this in recovery mode?  if so that only goes to a command prompt...ie...never loads the desktop (is that how its supposed to work)?

How do i get to a terminal screen to enter the commands that you gave me for the recovery.

---

### Post by mgmiller on 2007-10-12
You won't get a desktop.  At the point where it is going backa and forth hit the ctrl, alt and F1 keys simultaneously and you shuold get a black Dos like screen asking for your log in.  Then proceed as above.

Alternatively,  you could boot off the Live CD and from that desktop, mount the Ubuntu hard drive, which should be listed in the Places > Computer area, by double clicking on it (at least that's how it works in Fiesty, I don't know if they changed it in Gutsy) and then seeing where it is mounted, for example, it may be mounted in /media/"drive" where "drive" is the name it gave to the disk.  Then, open a terminal and cd to the X11 directory on that drive.  For example:
```
cd /media/"insert drive name here"/etc/X11
```

you can do the command:
```
ls
```

to make sure you are in the right place.  
You should see your backup file and the original and maybe a few other things.

Then, copy the backup over the changed file:
```

sudo cp xorg.backup xorg.conf
```

where xorg.backup is the name you gave to the backup file.

After that, just reboot and you should be good to go.

---

### Post by K5KS on 2007-10-16
Nothing here made any difference in clearing up the display.  I hacked away at this file countless times.  At one point I was just plain malicious about it.  I was able to back it up fine.  Gutsy offers a much better GUI for working with drivers.  You are able to select some specifics.  It even added the additional code that the Neomagic driver page suggested.  That was not there before.  Even after that no luck.  

does anyone think that it just cant be done?  Is there a limitation?  

I did find a good web page for explaining the different options in the xorg.conf file.  here it is if anyone has any ideas please let me know [http://driver2.sis.com/linux/XF86Config ]("http://driver2.sis.com/linux/XF86Config")

also here is a blurb about the card: MagicGraph 128XD (NM2160)
[INDENT]
The driver supports depths 8, 15, 16 and 24 for all chipsets except the NM2070 which does not support depth 24. All depths are accelerated except for depth 24 which is only accelerated on NM2200 and newer models. All visuals are supported in depth 8. TrueColor and DirectColor visuals are supported in the other depths. [/INDENT]

Any thoughts on that?

---

### Post by mgmiller on 2007-10-17
I did suggest a while back that you try adjusting brightness and contrast.  Did you experiment with that?  Maybe a lower brightness and higher contrast.

I also looked up some more specs for your card and there are a number of different refresh rates that it can run.
Specifically, 16 bit is 64k colors.  The following info is taken from a Gateway tech support page for your notebook:
[http://support.gateway.com/s/Mobile/Solo_Series/p2300/p230053.shtml]("http://support.gateway.com/s/Mobile/Solo_Series/p2300/p230053.shtml")

To summerize, the lines for 800x600 at 64k colors can use the following refresh rates:
Dot clock Mhz ..........Horizontal freq. KHz..............Vert. freq. Hz.
  40.0........................................37.8.......................................60
  50.0........................................48.1........................................72
  49.5.........................................46.9........................................75
  56.25......................................53.7........................................85

I don't know how to directly change the Dot clock, but if you select the appropriate horizontal and vertical frequencies, that should change it. 

This gives you 4 more changes you can try, each of which will give a different refresh rate at the same color depth and resolution.  refresh rates can definitely  affect the clarity of the display.  

Let me know if Gutsy lets you add these rfresh rate changes through its new gui.  Used to be, you had to do do a 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then give it the horizontal and vertical refresh rates.

You can also just edit your xorg.conf and stick them in the mode line.
You have been hacking around a lot with your xorg.conf, so maybe try it that way.

Don't forget to keep a backup of a config that works, just in case.

 
On a lighter note, you have learned a lot about your hardware and some of the ins and outs of the operating system, so this exercise was not all bad.

Could you post a digital picture of what your monitor looks like?  Not a screen capture, but an actual digital picture taken with a camera.  Use a tripod or other way to stabilize the camera and don't use the flash.  Then we can all see what you are seeing.


Good luck.  :popcorn:

---

### Post by K5KS on 2007-10-17
I am not sure what expression to use here...Holy Crap!!!  it is working.  Many Many thanks to mgmiller for sticking with me over the last week plus.  I knew that it could be done and as mg mentioned what an intro to Ubuntu/Linux.    

After messing with xorg.xonf and not being able to get the display to load once again!!!  I hit Ctl Alt F1 for the terminal screen.  after logging in and 4 unsuccessful attempts at restoring the back up.....I tried this command....and it seemed to work or at least do something.
> sudo dpkg-reconfigure -phigh xserver-xorg

This allowed me to get back in upon rebooting and when I pulled up the xorg.conf file it was reset or something because it was very simplified.  no Mode Line or multiple monitors in it.

 > The resolution was still fuzzy so I changed the display depth to 16

I logged out and restarted X and all was good when I logged in all was good.  I could tell as soon as the graphic started spinning.  This is the display that I remember having in the past.  

A couple of things...all of the documentation on the web said that this display could only go up to 800x600....very wrong I am running with 1024x768 and everything seems to fit a lot better.   Below I have posted the finial version of my xorg.conf...I hope that helps others as well.  

Another thing is the the reconfigure gave me new
 HorizSync 28-52 (previously was 31.5-37.9)
VertRefresh 43-60 (previously was 56-65)


> # xorg.conf (xorg X Window System server configuration file)
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
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
        Identifier      "Neomagic Corporation NM2160 [MagicGraph 128XD]"
        Driver          "neomagic"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Neomagic Corporation NM2160 [MagicGraph 128XD]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Thanks for eveyone's help especially mgmiller.  

Now on to my next Ubuntu install!!!

---

### Post by mgmiller on 2007-10-18
:lolflag:

Glad I could help.
Welcome to Ubuntu!

As you noted in the changes to your xorg.cof, this was a refresh rate issue.
I am also surprised it's doing 1024x768, as all the info I could find said your card tops out at 800x600.
It would appear the Linux driver does a better job than the Windows driver in this instance.
I am curious, in System>Preferences>Screen Resolution, what refresh rate does it say now?  And do you know what it said before?

Also, just in case, make a backup of your new current working xorg.conf and you can probably get rid of the older backups you made.

---

### Post by Scroobytec on 2007-10-18
Hi There 

to improve your fonts in Feisty try this, I found it some time back and it works: **[http://www.howtoforge.com/sharp_fonts_gnome](http://www.howtoforge.com/sharp_fonts_gnome)**


I also used it on Gutsy with success.


\\:D/

---

### Post by K5KS on 2007-10-18
> I am curious, in System>Preferences>Screen Resolution, what refresh rate does it say now?  And do you know what it said before?

It is set at 60.  options are for 56/60. This is the same as it was before.  I believe that the fix was to reconfigure and then it was a simple adjustment on the depth.  

I am not sure why the original install was such a difference in the hor/ver refresh rates.  I do know that it can really mess up the screen appearance.  I wish I had taken a picture so you could see before and after.  There is some Wow!! factor.  

thanks for all the help!!

---

### Post by mgmiller on 2007-10-18
The only thing I can think of is that because this is Gutsy and you installed the beta, something changed over the last week or 2 in the many updates you received.  Then when you had the system rescan the xorg.conf file, the new Gutsy changes "just worked".

Glad it worked out.

---


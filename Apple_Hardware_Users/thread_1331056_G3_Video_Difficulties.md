---
title: "G3 Video Difficulties"
date: 2009-11-18
forum: Apple Hardware Users
---

### Post by RealEmotionX on 2009-11-18
Alright, I have tried my best to solve this problem on my own but no matter what path I take I end up stuck.

So here is where I am~

---I use this link
[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)

To try and get a system running, when I try the first option this happens....

Xubuntu starts to boot up, it starts to show what is going through the xubuntu load up process, but gives me a black screen with the white line at top THEN gives me a black screen with nothing. The disk sounds like its doing something so I let the machine run in the hopes it will change.

I start the machine in [live-powerpc video=ofonly] to force it into low video mode and I get a boot up screen similar to the last one, but with a white bar on the bottom on the screen. Eventually It boots into this mess instead of the LIVE CD

[IMG]http://i47.tinypic.com/242g3e8.png[/IMG]

So, I just ignore it and continue with the directions and proceed into the Command line with ALT-CNTRL+F1

and type [sudo nano /etc/X11/xorg.conf]

Great, the config file is all there, and I go to make these changes

> Look in the file for the "Modules" Section in there you should have one that says

Load "dri"

change that to

#Load "dri"

Then look towards the bottom of the file for

HorizSync

and

VertRefresh

change the values of these to

HorizSync 58-62

VertRefresh 75-117

Then I output changes and exit the Nano editor.


Then I put this in just like the thread says to keep moving
[sudo killall -HUP gdm]


The terminal flashes black three times and then I get this

[img]http://i49.tinypic.com/9ps4uh.png[/img]

At this point I cant go any futher with the tutorial, so I hit YES on the message which asks "Would you like to view the X server output to diagnose the problem?"

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System: Linux 2.6.15-22-powerpc64-smp ppc
Current Operating System: Linux ubuntu 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc
Build Date: 16 March 2006
    Before reporting problems, check http://wiki.x.org
    To make sure you have the latest version.
Module Loader Present
Markers: (--) probed, (**) from config file, (==) default setting 
         (++) From command line, (!!) Notice), (II) informational
         (WW) warning, (EE), Error, (NI, not implemented, (??) unknown

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 19 04:13:37 2009

(==) Using config file: "/etc/X11/xorg.conf"
```

I hit <OK> and then it asks "Would you like to view the detailed xorg output as well?" and I hit OK and it gives me the same data

I hit <OK> and it says [The X server is now diabled. Restart GDM when its configured correctly] 

I hit ok, and am returned to the command line.

---

### Post by llamabr on 2009-11-19
Hi.  Sorry for the lateral answer, but on my G3, I had too much trouble with ubuntu, who don't directly support ppc, so I installed debian lenny, which runs perfectly, and installed with no trouble, first time.

---

### Post by RealEmotionX on 2009-11-19
I want to run XFCE and use the machine for light internet browsing, wont debian just give me a command line?

---

### Post by linuxopjemac on 2009-11-19
> wont debian just give me a command line? 

of course not, Lenny gives you a graphical interface too (depending on what you want, XFCE, Gnome, KDE etc.)

---

### Post by dull.neon on 2009-11-19
RealEmotionX: Sorry to hear about your installation woes...

> ...but on my G3, I had too much trouble with ubuntu, who don't directly support ppc...actually, ubuntu 9.04 installed beautifully on my ibook g3 (with *live-nosplash-powerpc*). i went into an overly enthusiastic apt-get mode to try and speed things up and screwed everything.

> ...so I installed debian lenny, which runs perfectly, and installed with no trouble, first time.i actually went this route first - i used [this image (http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-xfce+lxde-CD-1.iso) to]("http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-xfce+lxde-CD-1.iso") [burn a CD installer]("ttp://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-xfce+lxde-CD-1.iso"). it installed debian and XFCE4 by default. (the regular debian PPC images install gnome.) fast and snappy. would recommend it over xubuntu. the only reason i didn't stick with it was i just couldn't figure out power management properly, like figuring out how to make my ibook sleep when i shut the lid. 

alternatively, you could install a basic (x)ubuntu install via the alternate ISOs and then use aptitude to get the XFCE and build up your system somewhat more optimally and incrementally. (this is what i ended up doing after screwing myself the first time around.) this is somewhat time consuming and i needed another machine to surf for answers and help (did that via my phone), so your milage may vary depending on how much time and patience you have.

hope this helps.

---

### Post by RealEmotionX on 2009-11-19
alright, I will give lenny a try, though for the sake of progress, if anyone has any other tips for Xubuntu, to get it to run for other people, toss it my way and I will probably try it too.

---

### Post by RealEmotionX on 2009-11-19
Debian Lenny is giving me video problems, but not as bad. I can view the xorg error clearly

SCREEN NOT FOUND. Or something similar, I am not right in front of the machine.

---

### Post by oswaldkelso on 2009-11-19
> **RealEmotionX said:**
> Debian Lenny is giving me video problems, but not as bad. I can view the xorg error clearly

SCREEN NOT FOUND. Or something similar, I am not right in front of the machine.

[http://forums.debian.net/viewtopic.php?f=16&t=26577](http://forums.debian.net/viewtopic.php?f=16&t=26577)

You will need to find out your screen resolution first before you can set it

[http://www.everymac.com/](http://www.everymac.com/)

---

### Post by RealEmotionX on 2009-11-19
getting a parse error on line 43 in section 'screen'

[["Default" is not a valid keyword in this section]]

Removed the word Default from "Default Screen" for kicks, and it still spits the same error out, and thats the only line with the word default.

---

### Post by oswaldkelso on 2009-11-19
post your xorg.conf it sounds like you've made a typo 

also check your /var/log/Xorg.0.log

---

### Post by RealEmotionX on 2009-11-19
is there anyway to SSH into it so I can copy and paste? It wouldn't be fun to go and retype all the lines. Not that this process has been fun (Well maybe a little.)

---

### Post by linuxopjemac on 2009-11-20
you can try to automatically make an xorg.conf file:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by oswaldkelso on 2009-11-20
> **linuxopjemac said:**
> you can try to automatically make an xorg.conf file:

```
sudo dpkg-reconfigure xserver-xorg
```

Try su not sudo. sudo is on by default in Ubuntu not in Debian. I don't use it at all.

Also see the Debian imac how to in my sig. Whilst most things are the same for PPC. Differences exist. There are also complete xorg.conf files for both tray and slot loader imacs. you can compare with yours.

---

### Post by linuxopjemac on 2009-11-20
thanks oswaldkelso, I didn't know that...

---

### Post by RealEmotionX on 2009-11-20
I will type it out by hand tonight and let you guys see what I did, and then compare your links to my xorg.conf. ^_^

Debian wouldn't let me operate in sudo, saying the user is not in the sudoers list, so I went ahead and logged in to root until this scenario is resolved.

and dpkg-reconfigure will just give me a configuration that doesnt work.  Tried it.

---

### Post by linuxopjemac on 2009-11-20
what kind of G3 you exactly have ? Maybe people have a working Xorg.conf for you here...I have a Pismo G3 with Debian Lenny. You could have it if you want....

---

### Post by RealEmotionX on 2009-11-20
its a Graphite iMac G3 600MHZ
[http://www.everymac.com/systems/apple/imac/stats/imac_se_600.html](http://www.everymac.com/systems/apple/imac/stats/imac_se_600.html)

---

### Post by linuxopjemac on 2009-11-20
[http://www.debianadmin.com/fix-for-sleepy-display-and-boot-to-prompt-on-imac-g3.html](http://www.debianadmin.com/fix-for-sleepy-display-and-boot-to-prompt-on-imac-g3.html)

??

sorry, forget it , you have rage 128

---

### Post by linuxopjemac on 2009-11-20
This is the xorg.conf you need I think....

[http://ubuntuforums.org/showthread.php?t=191080](http://ubuntuforums.org/showthread.php?t=191080)

---

### Post by RealEmotionX on 2009-11-20
You were right!!! It took some manual effort, and I exempted the server layout input and wacom related sections becuase I am lazy, but I have a full desktop now that is VERY snappy as far as I can tell from opening iceweasel and jumping onto my macbook to celebrate

FOR FUTURE REFERENCE. THIS SHOULD WORK UNDER XUBUNTU or DEBIAN LENNY
```
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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
# Load "i2c"
# Load "bitmap"
# Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "dbe"
Load "glx"
# Load "int10"
# Load "type1"
# Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Driver "ati"
Option "UseFBDev" "false"
Option "SWcursor" "true"
Option "ForcePCIMode" "true"
Option "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
Option "AIGLX" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection 
```

---

### Post by RealEmotionX on 2009-11-21
This is odd. I installed Xubuntu in favor over Debian which felt awkward, and this machine is for family use because of the PC that fried itself and...I install it, boot into low video mode, copy and paste teh exact xorg.conf that worked under debian, and the result is


FATAL SERVER ERROR
NO SCREENS FOUND

---

### Post by linuxopjemac on 2009-11-21
Debian is more suitable for PPC in my honest opinion. I would just stick to Lenny. You can do everything else as you can in Ubuntu, the only exception is that you need to wait longer for updates. Lenny is quite 'old' already. If you are brave enough, you can go to "Sid", which gives you the unstable and up to date version of Debian. If you just want a working system, stick to Lenny. I am a happy user of it on my G3 PowerBook.

I think the older versions of (X)Ubuntu used another xorg. Newer kernels work in a different way. Lenny still uses the old way I guess...I am not expert in this. Maybe someone else can give an explanation as to why the old xorg.conf only works for the older versions of (X)Ubuntu.

---

### Post by oswaldkelso on 2009-11-21
> **linuxopjemac said:**
> Debian is more suitable for PPC in my honest opinion. I would just stick to Lenny. You can do everything else as you can in Ubuntu, the only exception is that you need to wait longer for updates. Lenny is quite 'old' already. If you are brave enough, you can go to "Sid", which gives you the unstable and up to date version of Debian. If you just want a working system, stick to Lenny. I am a happy user of it on my G3 PowerBook.

I think the older versions of (X)Ubuntu used another xorg. Newer kernels work in a different way. Lenny still uses the old way I guess...I am not expert in this. Maybe someone else can give an explanation as to why the old xorg.conf only works for the older versions of (X)Ubuntu.

Since the newer xorg. 7.something The X window system is meant to fix the graphical display automatically. This is why there is no info in the xorg.conf file. Due partly to apple no being very open, it's harder for the devs to get this automatic system to work on PPC. This is why you need to create it manually. Things are also complicated because there are slightly different xorg.conf file needed depending on which exact model of imac you have. Tray loaders are easy they all seem to use the same xorg.conf file. Slot loaders seem to differ depending on the version of the graphics card. If we look at the this xorg.conf it works on the imac 600 (I suspect it will work on the 500 and 700 also) but there are 5 different graphics cards for the imac PPC. If anyone can offer a working xorg.conf with the model, I'll add it to my how to in my sig.
Find your model here.   [http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

---

### Post by RealEmotionX on 2009-11-21
okay, so the xorg.conf listed wont run in 9.04 but it takes in 6.06

---

### Post by oswaldkelso on 2009-11-21
I don't have a slot loader so can't confirm. But would envisage that that if it works for a 6.06  it should work for a 9.04. if were talking about the same machine. That said the new X broke my twin view on my G4 and I've never got it going again.

---

### Post by RealEmotionX on 2009-11-22
6.06's X config has stuff in it, 9.04 does not. 

6.06 upgrades successfully on the imac G3 SE to 8.04 (I think)

either way, the machine is working awesome on the upgrade, cept I broke firefox :( I gotta figure thatout.

---

### Post by oswaldkelso on 2009-11-22
As I tried to explain before. The newer X should not need the xorg.conf file to be populated. It's meant to be able to work it all out by it's self so it's empty. On PPC it doesn't. So on a fresh install it's blank. If you upgrade from an older version you will of course still have your working xorg.conf settings. 

If it's blank you need to edit your xorg.conf you need to restart the xserver. 

One of the main problems is not all examples of xorg.conf files work on all imacs. 

I see people claiming this xorg.conf works and that one works but I doubt they have all versions of PPC imac ;) 
I've tried to gather all claimed working xorg.conf files I've found. I've not edited them as I can't test them. If people could confirm what machine they have we could cover them all. I see many entries in peoples xorg.conf files that I'm dubious about. As in if they're required, used, ignored, etc, depending on the system and machine installed on. 

As far as I can tell there seem to be three main versions. see my blog.

[http://oswaldkelso.blogspot.com/2009/11/imac-xorgconf-ppc-all-versions.html](http://oswaldkelso.blogspot.com/2009/11/imac-xorgconf-ppc-all-versions.html)

---

### Post by linuxopjemac on 2009-11-23
Thanks for your effort oswaldkelso, I added your link on my web site under Linux/Apple links -> PowerPC.

---


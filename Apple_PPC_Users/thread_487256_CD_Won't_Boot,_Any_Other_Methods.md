---
title: "CD Won't Boot, Any Other Methods ?"
date: 2007-06-28
forum: Apple PPC Users
---

### Post by youngwun0 on 2007-06-28
Hello Everyone,

Now i recently aquired an iMac G3 for myself with Mac OS 9.2.2 and Mac OS X 10.3.9 Installed working just fine with cd-rom slot-load and all.... I am fairly new to this and was hoping to get into the whole linux scene so i was looking at ubunutu and openSUSE which both support PPC iMac's and such anyways,... I burned a copy of both ubunutu and openSUSE PPC versions hoping to get it to boot but when holding C or D or almost all the other startup tactics to boot up a CD hasn't worked for me :( I am deprete now and fail to give up i was told that my CD-Rom may be old and may not be able to boot burnt CD-Roms even though it boots audio CD's and everything else just fine except burnt bootable CD's.... Now i hope i am not going to bother anyone by asking this and i am sure it has been asked before although all i see is a bunch of jabber when i do search such as start bootx, move kernals here and there... i'm a big time linux newbie and i was wondering if there was anyway possible to boot linux or install linux on an iMac PPC G3 400 Mhz without the use of a cd or dvd ??? If so would anyone kindly point me to a good guide that can help a newbie like me ??? as i have seen a few things but all i see are these commands and things like make a partition and move kernals to this and that..... i'ts really fustrating and i am not up for reinstalling or deleting my Mac OS X installation :(

If anyone needs to know here are my mac's specs:
Apple iMac G3 Indigo (Model: M5521)
Processor: 400 Mhz G3 PowerPc
320MB Ram
10GB Hard Drive
CD-ROM Drive
Network: 10/100 Ethernet
Modem: 56.6k
Wireless: Airport Ready
Ports: 2 USB + 2 Firewire
Display: 15" Color (13.8" viewable, .28 dp, 95 Hz-800 x 600).
Onboard Sound With Headphone Jack
Operating System: Mac O/S/X 10.3.9 And Mac O/S 9.2.2 Installed

---

### Post by pxwpxw on 2007-06-28
Hi,

Your imac should be able to boot from CD, can you post a list or picture of the files you see when you open the ubuntu cd in macos?

---

### Post by youngwun0 on 2007-06-28
I know, It just doesn't like ANY kind of burned bootable disk, when i place it in it doesn't show up on my desktop as it would any other cd, it just leaves it in the slot and ignores it lol so i can't really tell you what files are on but i know it was burned poperly,

Anyhow i have been reading your guide on booting from the hard drive and am a little lost, so i downloaded the 4 files your guide says to.... vmlinux, initrd.gz, yaboot, yaboot.conf Firstly when i right click and save vmlinux and yaboot it saves as a .htm file i have tried booting open firmware with and without the htm extension but when i enter 0 > boot hd:0,yaboot it gives me a error message something like "Load size is too small" and "nonsupported load size" any idea where that may be coming from ? the files are copied onto the Macintosh HDD folder alongside my system folders and such as the guide stated...

Thanks for the quick response, i see you deal with people like me each day and you seem very very helpful, hopefully i can get this running so i can be able to teach others as well :)

---

### Post by pxwpxw on 2007-06-28
You have a typo - boot hd: but thats not all - you have to find what partition number to boot from,
 then you do
```
 
boot hd:x,yaboot

```

where x is the partition number where you have vmlinux (just change the name back) initrd and etc, and your cd iso imag if using an iso./.
You get your macos partition number using diskutil from a terminal ins macosx. 

```

man diskutil ## for info
 diskutil llist

```

I have to vanish now, will ceck back in a few hours.

---

### Post by youngwun0 on 2007-06-29
Ok so thanks to you i have made some progress but i am still not there yet... so i downloaded the 4 files as ubunutu's guide stated and removed the .htm extension from the 2 files that had .htm at the end (which were yaboot and vmlinux) I copied all the files to my "Macintosh HDD" which i found out was partition number "9" i downloaded the ubunutu PPC version and copied to also to the "Macintosh HDD" with the other 4 files and named it ubunutu.... next i restarted the iMac and did as the guide stated and typed "boot hd:9,yaboot" i was instantly moved to a new command area called the yaboot or whatever, it said boot: and i typed install... when i typed install and pressed returm it came up with this error:

please wait, loading kernal
install:9 lumlinux: unable to open
invalid device

or something of that sort, one other question i have is will this delete my entire mac os x installation ? I don't mind too much as i am getting bored of it and i have a backup but it would be nice to have it there, i never created a partition for ubunutu so idk if it will delete after this error gets fixed (if you help me)

anyways i know were not done but i just wanted to tahnk you again for taking the time out to help me :)

---

### Post by pxwpxw on 2007-06-29
install:9 lumlinux: unable to open

thats a typing error if it is truly the errror message.

In macos, open yaboot.conf and post the text.

---

### Post by youngwun0 on 2007-06-29
hey bro, I just finished installing it BUT for some reason after installation and restarting it loads and starts everything but stops at "running local boot scrict" I can press enter and log in but all i get is a command terminal or something :( anyway to fix this or get into the ubuntu desktop ?

---

### Post by pxwpxw on 2007-06-29
Hey, thats OK. Type 
```

df
ls -l
uname -a
ps ax
man apt-get

```
What did you install? Sounds like the server or CLI version,if so you can install a full desktop, about another 1GB.

---

### Post by youngwun0 on 2007-06-29
hey, sorry but what shall i do after entering those commands? i get a page of writing but no instructions.

---

### Post by pxwpxw on 2007-06-29
Yes, I just meant you to have a look at them, the part we need is from
```

 df
 uname -a

```
 df will show you what disk space available and  used so far
 uname will give you the kernel version.
 you need to get that to see if you have plenty of space for the desktop.

---

### Post by youngwun0 on 2007-06-29
oh sorry, it says i have only used 1.2GB out of 10GB, the kernel says ubuntu 2.6.20-16-Powerpc #3

---

### Post by pxwpxw on 2007-06-29
Ok, sounds like you did a server install, confirm please.

---

### Post by youngwun0 on 2007-06-29
I think i did, i thought i chose desktop though :(

---

### Post by pxwpxw on 2007-06-29
Well,  dont want to try to install a desktop if one already there.
Try this just to check on that:
```

startx

```
and wait a minute or so to see if anything happens.

And what ubuntu variety was the cd - ubuntu, kubuntu, xubuntu?

---

### Post by youngwun0 on 2007-06-29
it says startx is not installed, the installation was ubuntu for sure

---

### Post by pxwpxw on 2007-06-29
right, you can install a desktop using apt-get as below, and it will do most of that using the desktop that the install cd has, if it is the same desktop. Otherwise it will try to download from the network, possibly 200MB or so. If you have a slow ubuntu mirrror it might be slow.
```

 sudo apt-get update
 sudo apt-get install ubuntu-desktop.

```
Ubuntu-desktop is a big gnome one; xubuntu-desktop is compact, i like it;  kubuntu-desktop is big too but kde istead of gnome.
 Hope that all makes sense.

---

### Post by youngwun0 on 2007-06-29
I finished the installation and all is well but when it prompts me to login i can barely see the screen enough to enter my password and username, this also happens on the desktop, it's dull grey and has lines in going down all over with no kind of color, i heard something about editing a file called xorg.conf or something to fix the video, anyway to fix this ?

once again thanks for the help so far

---

### Post by youngwun0 on 2007-06-30
Bump..... sorry guys, I'm still having the trouble stated in the above post, i have been locked out of my mac for a good 24 hours already due to the screen screwing up after installation :( if anyone knows a solution for this greyish screen with lines going down after installation any help would deeply be appreciated.

---

### Post by pxwpxw on 2007-06-30
Thats good, and as you say, only needs some tweaking of /etc/X11/xorg.conf. But I am not sure what exactly is needed, so before you try any changes please post a copy of the text from your xorg.conf. Can you do that?

You can use a terminal window from the desktop, or you can switch to a console using
 Control Alt F2
 (function key F1 to F6) 

If you have to use the console, you can use nano to read and save a copy of xorg.conf to <some file name>. Dont try to change xorg.conf at this stage.
```

 nano /etc/X11/xorg.conf

```

---

### Post by youngwun0 on 2007-06-30
Hello again,

Now i cannot see much because of the screen but i can see enough to get into the desktop and use the terminal, i ran that line  in the terminal and got the following, i wasn't sure how to save/backup the entire thing from the terminal so i copied and pasted, here it is:


```
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
        Option          "XkbOptions"    "lv3:lwin_switch"
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
        Identifier      "Generic Video Card"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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
```

---

### Post by pxwpxw on 2007-06-30
This should do it.
 PowerPCFAQ.

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
5.2 How do I get Ubuntu working on an iMac G3?

Before editing, make a backup copy of xorg.conf

```

 cd /etc/X11
 sudo cp xorg.conf xorg.conf00
 cd

```

Only if it still needs work, you might need to change the resolution here.
But not if you have used 1024x768 with maximum colours. (You listed 800x600 in the 1st post)
```
 
Section "Screen"
### other entries.

     SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
     EndSubSection
EndSection

```
Delete the "1024x768" to limit to 800x600. Should not be necessary.

---

### Post by youngwun0 on 2007-06-30
did as told but after the restart nothing has changed :(

---

### Post by pxwpxw on 2007-06-30
Just saw your post. Is the display stable (any jitteing or tearing) and could you  describe what else is wrong.
Is screen ok when you change to command line console using Ctrl Alt F1?
Have you rechecked xorg.conf to make sure you got what you set?

What resolution have you set in xorg.conf?

And best if you can post the new 
 /etc/X11/xorg.conf

and also the log from

 /var/log/Xorg.0.log

will sshow if something is wrong.

---

### Post by youngwun0 on 2007-06-30
Hmm well the display is stable but a very dull grey and when i move the mouse everything turns different shades of grey, it is hardly viewable and no color at all, it looks fine when i'm in the command console it happens only in the login area for the desktop and the desktop itself. i have rechecked anafter rebooting and it seems like it was saved properly i have set 1024x76 as that is what i have always ran with no problems and full color on my mac, the only things i have done to the xorg.conf were adding the # symbol to the start of the line with load dri and i changed the ver and dor line numbers as the guide stated, here is thwhat i get when i attempt to view the log file:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-16-powerpc #3 Thu Jun 7 19:32:55 $
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 30 09:49:34 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc,
        /usr/X11R6/lib/X11/fonts/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/X11R6/lib/X11/fonts/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open APM successful
(II) Loader magic: 0x101d6f08
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.1
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:0b:0: chip 106b,0020 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:10:0: chip 1002,5052 card 1002,5052 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:11:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:16:0) ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS rev 0, Mem $
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [1] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [2] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [3] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


```

---

### Post by pxwpxw on 2007-06-30
Did you get the # dri and eveything right then.
Best to post the xorg.conf too.

yes while I am reading that, could you ge the video driver type this way

```

 lspci | grep VGA

```

Maybe just that is part of problem.

Need to get the whole log file. Do it this way. Read it first.

Open a terminal on the desktop 
```

 cat  /var/log/Xorg.0.log

```

Then you should be able to select all of that text and get it out as you did before.  
 You can also use 
```

 less <filename > 

```
for just reading files.

---

### Post by youngwun0 on 2007-06-30
2 questions before doing so.....

what do you mean by type it this way ?:
```
 lspci | grep VGA
``` 

i typed that in termininal but no results i copied and pasted it

also how would i be able to reopen my minimized windows when i minimize them, is there a button to re-maximize ? the reason i ask is that i find myself switching back and forth between the termininal and firefox and because of the screen being messed up i cannot copy the log and xorg.conf and go back and forth without doing it one at a time.

---

### Post by youngwun0 on 2007-06-30
Here is the log file:

```
jay@ubuntu:~$ cat /var/log/Xorg.0.log

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-16-powerpc #3 Thu Jun 7 19:32:55 UTC 2007 ppc
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 30 10:33:30 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc,
        /usr/X11R6/lib/X11/fonts/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/X11R6/lib/X11/fonts/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open APM successful
(II) Loader magic: 0x101d6f08
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.1
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:0b:0: chip 106b,0020 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:10:0: chip 1002,5052 card 1002,5052 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:11:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:16:0) ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/26, 0x90000000/14, I/O @ 0x0400/8, BIOS @ 0x90020000/17
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [1] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [2] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [3] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [1] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [2] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [3] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [5] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [6] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [9] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.2.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.3.1
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00:10:0
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.0.2
        ABI class: X.Org Video Driver, version 1.1
(II) FBDEV(0): using default device
(II) Running in FRAMEBUFFER Mode
(**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
(==) FBDEV(0): RGB weight 888
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: OFfb ATY,Rage12 (video memory: 768kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0):  mode "1024x768" ok
(II) FBDEV(0):  mode "800x600" ok
(II) FBDEV(0):  mode "640x480" ok
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
(**) FBDEV(0):  Built-in mode "current": 100.0 MHz, 94.0 kHz, 116.3 Hz
(II) FBDEV(0): Modeline "current"  100.00  1024 1040 1048 1064  768 784 792 808 -hsync -vsync -csync
(==) FBDEV(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(==) Depth 24 pixmap format is 32 bpp
(==) FBDEV(0): Backing store disabled
(**) Option "dpms"
(**) FBDEV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:lwin_switch"
(**) Generic Keyboard: XkbOptions: "lv3:lwin_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list! 

```

here is the xorg.conf after edit:
```
jay@ubuntu:~$ cat /etc/X11/xorg.conf
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
#       Load    "dri"
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
        Option          "XkbOptions"    "lv3:lwin_switch"
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
        Identifier      "Generic Video Card"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       58-62
        VertRefresh     75-117
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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

```

here is a screenshot as i managed to do that: http://img518.imageshack.us/img518/832/screenshotzz3.png[/img]

---

### Post by pxwpxw on 2007-06-30
Overlapped yours - let me read it.

I think I see it its the Modeline in the log is wrong for your display. 
Modelines can ge generated using "gtf"

admax@bigmac:~$ gtf 1024 768 75

  # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

is what should be used, this has to be added to the xorg.conf. I will have to check that out, goes in the monitor section, I will do that in next post, take a 1/2 hr or so to check. 

The modeline in the log is not even close.

Sorry about corrections, having bad delays here.
XXXXXXXXXXXXXXXXXXXXXX

---

### Post by youngwun0 on 2007-06-30
I tried the Xorg.0.conf file but could not find one in the var/log/ folder when browsing from attachment, i tried uploading /var/log/Xorg.0.log instead but the upload said it failed, if you want to take a look at that /var/log/Xorg.0.log file i uploaded it to a different site here it isP: [http://www.yousendit.com/transfer.php?action=download&ufid=849A08CF3725F4E6](http://www.yousendit.com/transfer.php?action=download&ufid=849A08CF3725F4E6)

---

### Post by pxwpxw on 2007-06-30
I have the Xorg.0.log thanks, good idea sending file. Having probs here with the net.

I made a typo - Xorg.0.log is correct. I will post the info you need for the modeline shortly.

---

### Post by pxwpxw on 2007-06-30
This is the modeline generated by gtf ("man gtf" will explain), you can do this also.

$ gtf 1024 768 75

  # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
============

In /etc/xorg/conf

1. **Change the Monitor section** to use the modeline. I have also changed the gtf modeline sync +- settings. I may be wrong.
(Comment out the HorizSync and VertRefresh)
 
Section "Monitor"
        Identifier      "**imacg3**"
        Option          "DPMS"
	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
	Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -hsync -vsync -csync

##        HorizSync       58-62
##        VertRefresh     75-117
EndSection

2. **Change the Screen section Monitor to match the changed Identifier**.

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "**imacg3**"
        DefaultDepth    24

=====================
3. The only other thing is to try changeing the video driver to "ati", but I dont think thats the problem so just try the modeline first - **do  both 1 and 2 above.**

For ati driver: 
Section "Device"
        Identifier      "Generic Video Card"
###        Driver          "fbdev"
        Driver          "ati"
EndSection
=====================

---

### Post by youngwun0 on 2007-06-30
alright so i opened terminal and edited the xorg.conf file i deleted the monitor part and pasted what you put as #1, when i restarted i got an error saying no screens found, i dont thing or the right way :(

---

### Post by pxwpxw on 2007-06-30
OK, can you get back to something usable?

There was a change needed in part 2. to the Section "Screen"

---

### Post by youngwun0 on 2007-06-30
yes, the command console

---

### Post by pxwpxw on 2007-06-30
If you did not make the change in Section "Screen" Monitor "imacg3"
that would kill it. Do you want a new Section "Screen" so you can paste or can you just edit with nano??

---

### Post by youngwun0 on 2007-06-30
i didnt do the screen edit (forgot) i can do it in nano but when i type: nano /etc/X11/xorg.conf in command console i get a blank nano page to edit, i cant copy and paste anything from here because im on my phone internet

---

### Post by pxwpxw on 2007-06-30
Ok i will post a copy of the Section "Screen" to be sure.
When you edit with nano you must use sudo to allow it to be saved.
```

 ls -l /etc/X11/xorg* 
## that wil show xorg.conf if it is there.
 sudo nano /etc/X11/xorg.conf
## should then let you edit it, blank page means file not there,

```

See 2. in the post above.
 
You only need to change  Monitor "Generic Monitor" to Monitor "imacg3"
 in this secion, it must be the same name as used in Section "Monitor". 
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         **"imacg3"**
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```
==========================================

---

### Post by youngwun0 on 2007-06-30
added it but still nothing, just a blank nano page, i didnt delete it and know its there, i dont even get the password prompt like it should when i put sudo

---

### Post by pxwpxw on 2007-06-30
Ok, I know its difficult, just needs sorting out how to ge the xorg.conf corrected.
I will have to leave it for now itis 0455 here, time for  a sleep. Have a good read of the stuff above, on last thing, 
```

 ls /etc/
 ls /etc/X11
 ls -l /etc/
## you can probably get the idea from that, shoudl find xorg

```

I will be back after some sleep.

---

### Post by youngwun0 on 2007-06-30
Hey bro,

I just found out that i was typing "ect" instead of "etc" when trying to view the xorg.conf file so i got that part sorted out and now i'm back in the desktop BUT the monitor is still crappy even after doing the edits from the ubuntu site wiki and the 2 that you mentioned with putting "imacg3" in both the monitor and screen sections, i may be doing the edits wrong sbut maybe not, here is what my /etc/X11/xorg.conf file looks like after the edits you and ubuntu say to put:

```
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
#       Load    "dri"
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
        Option          "XkbOptions"    "lv3:lwin_switch"
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
        Identifier      "Generic Video Card"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "imacg3"
        Option          "DPMS"
#       1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk 81.80 MHz
        Modeline        "1024x768_75.00" 81.80 1024 1080 1192 1360 768 769 772 802 -hsync -vsync -csync
#       HorizSync       58-62
#       VertRefresh     75-117
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "imacg3"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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
```

Is this correctly formatted ? If not would it be possible for you to post the code changed to what you are speaking of here so i could delete the current coding and paste the modified correct way ? Thanks man i'll be waiting until you get back, here is the link to the filxorg.conf file as well in case your browser is still acting up: [http://download.yousendit.com/A278207F4571FB14](http://download.yousendit.com/A278207F4571FB14)

---

### Post by pxwpxw on 2007-07-01
Looks OK, but apparently its not the answer.
I think I know the problem, will give you another xorg.conf to try.
Please save a copy of the Xorg.0.log I wnt to see what it did.
Does your iMac have firewire ports? If not, its the original version, video spec is different.
More soon.

---

### Post by youngwun0 on 2007-07-01
Problem is fixed for the most part, thanks to your patience and help i now have a nice fresh OS running and it's viewable.... all i did was change the default bit depth from 24 to 8, i was playing with the xorg.conf for hours and learned alot (thanks to you) anyway one thing i noticed is that although the screen is way more viewable, the display is a bit fuzzy and the mouse cursor has a tiny invisible red box around it, here is a screenshot: [http://img412.imageshack.us/img412/3654/screenshotdb4.png](http://img412.imageshack.us/img412/3654/screenshotdb4.png)

this is the coding from my changed xorg.conf:
```
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
#       Load    "dri"
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
        Option          "XkbOptions"    "lv3:lwin_switch"
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
        Identifier      "Generic Video Card"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       58-62
        VertRefresh     75-117
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    8
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024-768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024-768" "800x600" "640x480"
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
```

---

### Post by pxwpxw on 2007-07-01
Yes, thats what I thought, in fact you should be able to use depth 16 or 15. The original iMac spec is  16 bit colour at 1024x768 with a 2MB videoram (standard). The 1999 version does 32bit.
You could also try using the "ati" driver. Do you want anymore xorg.conf versions, got some here if you do.

Screenshot looks good.

Might be  a bit sharper using the modeline or the ati driver, that fbdev modeline in the log seemed to be a way off spec for the iMac.

---

### Post by youngwun0 on 2007-07-01
Sure i'll take the ati versions if you have any better, i think i may be able to deal with this it's not THAT horrible but it is a littl fizzy and some of the colors are way off especially when it comes to blue colors... thanks again bro :)

---

### Post by pxwpxw on 2007-07-01
Here you are, you know enough now to keep out of trouble I think. 

Read the 2 of these you will see the options.

2 attachments are xorg.conf renamed to  xorgconf03.txt and xorgconf04.txt for upload to forum attachment (forum wants .txt files).

03 uses "fbdev" driver, 04 uses "ati" driver. Both are set for colour depth 16, may need 15. Keep them  as backups. You will have to copy/rename to xorg.conf after making a backup of your current good xorg.conf.

---

### Post by youngwun0 on 2007-07-01
Hmm, well i tried the first in both 16 and 15 depth but when i tried the second i got an error and got locked out, i fixed the code up a little, got back in the desktop and put back the backup i saved before that.

also i have a pretty newbish question.... when i try to add one of the saved files to the /etc/X11/ directory i get an error saying i don't have the permissions to move or change files, i have ran linux servers before via ftp but not desktop, any idea how i could go about either changing permissions or getting root to make such changes as moving files and renaming ? I had been having to run sudo nano and backspace all the text then copy what you had written but it's getting tiring lol

---

### Post by pxwpxw on 2007-07-01
Sounds interesting, was that the ati version that bombed? Would like to know.
You can select either of the monitor sections from Section "Screen".
There is a bit of explanation in man xorg.conf,  and man ati. 

The permissions  question - if you are talkiing about Desktop file manager, in xubuntu I just open file manager from a terminal as root, and from there can do moves, edits, most things -
```

 gksu <file manager>

```

Think its nautilus in ubuntu.
Was that the question?

---

### Post by youngwun0 on 2007-07-01
Yeah the ati one bombed, i will read some of the man xorg.conf and man ati, for now it isn't mission critical so i won't sweat it too bad, hopefully it being  just a little fizzy and weird on the colors will not screw up my monitor now or in the long run ?

yeah thanks, i got root and did it as you said using nautilus running this command in terminal:
```
 gksu nautilus
```

Thanks again bro, you have been a BIG help, i have learned alot through these past few days :D

---

### Post by youngwun0 on 2007-07-01
It's strange how most of the problems with the imac g3 i have read about on google consist on black screens on login of the desktop and the desktop rather then just a ugly fuzzy screen like my problem, i kinda wish i could fix it although it is viewable with the 8 depth it is kind of annoying and can hurt the eyes after a while.

---

### Post by pxwpxw on 2007-07-01
Cant you use depth 16, also try 800x600 at depthe 32

Some more thoughts, but no experience with iMacg3.


man fbdev
       For  this driver it is not required to specify modes in the screen sec&#8208;
       tion of the config file.  The fbdev driver can pick  up  the  currently
       used  video  mode  from the framebuffer driver and will use it if there
       are no video modes configured.

As I read this, your display settings in macos may be influencing the result, unless modelines are in xorg.conf. But I have not tested that idea, and not sure if this means modelines are ignored by fbdev.
 
Look at Xorg.0.log to see exactly what is happening with the video (AGP?) card as detected, and what modelines and colour depth are actually being used, and why the ati driver is nogo (man ati). I would have thought ati driver should work best, with max available resolution and color depth. The xorg.conf  atachments were untested here, may have a typo somewhere.
Certainly 8 bit (256 color) will give a poor result.

---

### Post by youngwun0 on 2007-07-02
Unfortunately i am pretty much a newbie at this linux thing as well as this whole monitor thing as i have never had this problem on any of my pc's or this mac so i do not know how to change the depth to 16 or the monitor resolution to 800x600 at depthe 32, i always seem to get 1024x768 for size and i don't get the dropdown menu to choose another size, not sure how to change it or what depthe is :(

---

### Post by pxwpxw on 2007-07-02
In the xorgconfo3 attachment, here is where you control it .
Here it is set to depth 16, and the Display subsection for depth 16 has Modes "1024x768" first on its list.
If you change the Default Depth to 24 here you would get  the Subsection with 800x600 resolution.  Also you can change the Modes "1024x768" "800x600" "640x480" round so that 800x600 is first etc. Only the first one counts here.
Hope that explains it. In the Macos, you should have a Colour and Resolution selection somewhere.

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "imacg3"
###     DefaultDepth    15
        DefaultDepth    16
###	DefaultDepth	24
        SubSection "Display"
                Depth           8
                Modes           "1024x768" 
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" 
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "800x600" "640x480"
        EndSubSection
EndSection

```

---

### Post by youngwun0 on 2007-07-02
hmm, strange.... i have removed the "1024x768" from all parts of the xorg.conf and still i get 1024x768 dimensions and only the 1024x768 option in screen resolution.

---

### Post by pxwpxw on 2007-07-03
I think this might be due to using the "fbdev" driver. As noted in my previous post, "man fbdev"  says  it gets some of its configuration from the Applemac firmware or video card, as last set up by Macos. I remember some such problem; fbdev is a bit confusing in this respect. The easy way to test this is to see what is your Macos display configuration and change it to  800x600 and "thousand of colours"  (Macos9 prefs popups, MacosX System Prefs, Display), or any other setting you like, then shut down and restart into ubuntu and see if Macos settings have prevailed. The otherr way to see what is happening is to look in the Xorg.0.log for Modeline or for 1024x768 - to see where it is geting that. 

With the ati driver, you should have more control - if it worked. The fbdev is a special driver with a  different way of interfacing with  video cards that support it.

You could also use Macos to observe results with a range of resolution and color, to see if your X windows quality concerns are simply due to running at low color range  (depth eight) instead of depth 16 (Thousands of colors in Macos language) or  depth 24 (Millions of colors)

I noticed a comprehensive thread on xorg.conf settings -

HOWTO: change resolution/refresh rate in Xorg.
[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by youngwun0 on 2007-07-04
The problem with that is that when i installed ubuntu i did a FULL partition, i'm pretty sure my entire HDD was whipped out and since my cd-rom works but will not boot cd's from it i am stuck now :(

---

### Post by pxwpxw on 2007-07-04
You should post a copy of your current xorg.conf and Xorg.0.log. I would like to see them, maybe can work out what is going on there.

---

### Post by youngwun0 on 2007-07-04
This is the xorg.conf file:

```
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
#       Load    "dri"
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
        Option          "XkbOptions"    "lv3:lwin_switch"
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
        Identifier      "Generic Video Card"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       15-20
        VertRefresh     10-15
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
###     DefaultDepth    15
        DefaultDepth    8
###     DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "800x600" 
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" 
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
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
EndSection

        Section "DRI"
        Mode    0666
EndSection
```

And this is the Xorg.0.log file:

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-16-powerpc #3 Thu Jun 7 19:32:55 UTC 2007 ppc
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  4 07:22:41 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc,
        /usr/X11R6/lib/X11/fonts/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/X11R6/lib/X11/fonts/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open APM successful
(II) Loader magic: 0x101d6f08
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.1
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:0b:0: chip 106b,0020 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:10:0: chip 1002,5052 card 1002,5052 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:11:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:16:0) ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/26, 0x90000000/14, I/O @ 0x0400/8, BIOS @ 0x90020000/17
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [1] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [2] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [3] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [1] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [2] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [3] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [5] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [6] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [9] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.2.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.3.1
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00:10:0
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.0.2
        ABI class: X.Org Video Driver, version 1.1
(II) FBDEV(0): using default device
(II) Running in FRAMEBUFFER Mode
(**) FBDEV(0): Depth 8, (--) framebuffer bpp 8
(==) FBDEV(0): Default visual is PseudoColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: OFfb ATY,Rage12 (video memory: 768kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0):  mode "800x600" ok
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
(**) FBDEV(0):  Built-in mode "current": 100.0 MHz, 94.0 kHz, 116.3 Hz
(II) FBDEV(0): Modeline "current"  100.00  1024 1040 1048 1064  768 784 792 808 -hsync -vsync -csync
(==) FBDEV(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(==) FBDEV(0): Backing store disabled
(**) Option "dpms"
(**) FBDEV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:lwin_switch"
(**) Generic Keyboard: XkbOptions: "lv3:lwin_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by pxwpxw on 2007-07-04
That is really strange, clearly fbdev is totally ignoring some xorg.conf settings, or it would not be working at all (the monitor settings HorizSync  15-20 and  VertRefresh  10-15 should not work at all)
 Dont change anything, I will try to find some more info on using the "fbdev" driver, I recall it needs the Section "Screen" contents to be set out in a specific way before you can get what you want.

One small check, what happens if you try to move the mouse cursor past the edges of the desktop (top, bottom or sides) Looks like you have a 800x600 window in a  virtual 1024x768.

If any fbdev experts are reading this and know the answer, please post.

---

### Post by youngwun0 on 2007-07-04
That is 1 thing i noticed, no matter what settings i use for HorizSync and VertRefresh nothing about it changes, i can put it to 0-0 on both and nothing..... on 8 depth (as i have) nothing will happen with the sides the screen is just very fuzzy and too little color in it but anything above that the mouse cursor will have to scroll over to the other side of the monitor.

i'm guessing that the fbdev ignoring has something to do with it :(

---

### Post by pxwpxw on 2007-07-04
I am reading about it now, probably needs extra vga setting  to be entered when it boots. Will post when I get something. Meanwhile make sure you have saved a copy of your best xorg.conf.
Would you run this to get your video card info -
```

 lspci | less

```
 the " | less"  will let you read the output if too many lines for screen.
One entry will be the video card.
It is probably AGP card ATI Rage or similar,

---

### Post by youngwun0 on 2007-07-04
This is what i get when running that command in terminal:

```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 Display controller: ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMD
S
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth FireWire (rev 01
)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (r
ev 01)
(END) 
```

---

### Post by pxwpxw on 2007-07-04
Got that thanks.
Could you please run again  each of the 2 xorg.conf versiion from the attachments xorgconf03.txt and xorgconf04.txt and post copies of the Xorg.0.log that you get after each one. It doesnt matter whether they work or not (but let me know) just need to see exactly what gets logged and what is differen between the 2, to make corrections. The ati driver is right for the Rage 128, so I must have got something wrong.
Also I am using the fbdev driver here on my iBook g4, no problem.

---

### Post by youngwun0 on 2007-07-04
Quick question... since the "xorgconf04.txt" produces an error and doesn't allow me to enter the desktop how can i copy the log from the command prompt and post it here ?

This is the log file after i changed it to xorgconf03.txt:

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-16-powerpc #3 Thu Jun 7 19:32:55 UTC 2007 ppc
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  4 20:04:02 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "imacg3"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc,
        /usr/X11R6/lib/X11/fonts/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/X11R6/lib/X11/fonts/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open APM successful
(II) Loader magic: 0x101d6f08
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.1
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:0b:0: chip 106b,0020 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:10:0: chip 1002,5052 card 1002,5052 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:11:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:16:0) ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/26, 0x90000000/14, I/O @ 0x0400/8, BIOS @ 0x90020000/17
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [1] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [2] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [3] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [1] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [2] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [3] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x90020000 - 0x9003ffff (0x20000) MX[B](B)
        [5] -1  0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [6] -1  0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [9] -1  0       0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.2.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.3.1
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00:10:0
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.0.2
        ABI class: X.Org Video Driver, version 1.1
(II) FBDEV(0): using default device
(II) Running in FRAMEBUFFER Mode
(**) FBDEV(0): Depth 16, (--) framebuffer bpp 16
(==) FBDEV(0): RGB weight 565
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: OFfb ATY,Rage12 (video memory: 768kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0):  mode "1024x768" ok
(II) FBDEV(0):  mode "800x600" ok
(II) FBDEV(0):  mode "640x480" ok
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
(**) FBDEV(0):  Built-in mode "current": 100.0 MHz, 94.0 kHz, 116.3 Hz
(II) FBDEV(0): Modeline "current"  100.00  1024 1040 1048 1064  768 784 792 808 -hsync -vsync -csync
(==) FBDEV(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(==) FBDEV(0): Backing store disabled
(**) Option "dpms"
(**) FBDEV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:lwin_switch"
(**) Generic Keyboard: XkbOptions: "lv3:lwin_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

---

### Post by pxwpxw on 2007-07-04
> **youngwun0 said:**
> Quick question... since the "xorgconf04.txt" produces an error and doesn't allow me to enter the desktop how can i copy the log from the command prompt and post it here ?


Yes understand the problem, Can you just save a copy form command line, and then get back into workable desktop to post. Also there should be an /var/log/Xorg.0.log.old which is the previous log.

```

cp /var/log/Xorg.0.log xlogsave

```

But I am more worried to know if you able to boot from a macosx or macos9 installer, I dont really know your situation about backup communication if your ubuntu install crashes - can you recover from that?  If your hard drive is big enough it miight be best to reinstall macosx on a small partition but depends on your situation.
In short, I dont really know the background of your problem with a cd install, that led you to do the hd-media install?

---

### Post by youngwun0 on 2007-07-04
Yeah i did a hd-media install because my cd-rom slot is old and will not boot burnt cd's or most mac os cd's including 9.x or mac os x.... therefore i am and can only run ubuntu at the moment unless i buy a new cd-drive or find someone to help me install mac os, i wish i knew a method other then cd/dvd or firefiwre to install mac :(

---

### Post by pxwpxw on 2007-07-04
Right.
First, you ran the xorgconf03 and according to the log, that set 16bit color, which should be clearly better than 8 bit (thousands of colors instead of 256). Comments?
Is it seriously worse than macos display was?

Second.
Does your iMacg3 have firewire ports, That would help cconsiderably.

---

### Post by youngwun0 on 2007-07-05
Yup it is worse then my mac os 9.2 and max os 10.3.9 display, before it was perfect, now it is very fuzzy and there is lots of color loss as you stated... i do have firewire ports for sure though.

---

### Post by pxwpxw on 2007-07-05
1. The screen shot you posted seemed usable to me. I'm not sure if you are saying you cant get back to that.

2. If you hav firewire, my info from apple tech papers says the iMac is 2nd generation and can boot from usb, and I think firewire. Also if you have access to another Mac, it might be possible to install from the other mac. And as a last resort, you could probably do a net boot via ethernet from yaboot on another  net connected mac, or possibly even a PC. I believe it is possible to install MacosX on usb and boot from that, a 4gb usb stick might be feasible for a backup (very slow though).
3. If nothing above works, a separate 1 GB partitin would be a safe rescue/reinstall option if you can get some space from ubuntu. You need to find out your partition map in ubuntu and how much space is now being used. Can tell you how if you wish to do that.

What do you think about all that?

---

### Post by youngwun0 on 2007-07-05
Yeah it seems usable but it is very fuzzy and as you said the colors are screwed up, grey shows good and so does a few regular colors but blue, red, yellow, orange ect.... show's ugly

I don't think i can boot from usb as i have read it has to be done by firewire using another mac, only problem is i do not know anyone around here with a mac or anyone in general anywhere with a mac, i would be interested in doing a net install through a pc even if it takes forever as that is all i have, i have 2 windows xp pc's and nothing else :(

if you have any further info on booting from usb, or using a pc to install that would be great, as of now i think i am stuck, i have 5.8GB free right now though.

---

### Post by pxwpxw on 2007-07-05
I think if you can live with the desktop, it would be best to get some secure backup on the iMac by downloading netboot images (similar to the hd-media ones) in ubuntu and copy them to another small boot partition which would be bootable using OpenFirmware (that is not the net boot from pc option, thats another issue). I am assuming you can download in ubuntu.

To see if that is feasible just need to see what partitions you have there, and whether you can change partitions from ubuntu with GParted, to make a small Apple HFS partition. Gnome Partioner is in Application->System on my xubuntu, some where similar in ubuntu.

In a terminal
```

 sudo mac-fdisk -l

```
Will show the partitons.

But you may think differently?

---

### Post by pxwpxw on 2007-07-05
[ Macintosh_CPUs-G3/iMac_26Oct99/iMac.pdf]("http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/iMac_26Oct99/iMac.pdf")

I can boot from  ubuntu(cli) on a 1GB usb stick, using open firmware boot, just now tried it on iBookG4, should be possible to do the same on iMacg3.

---

### Post by youngwun0 on 2007-07-05
This is what i get when i enter the fdisk command in terminal:

```
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           19052735 @ 2018     (  9.1G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                 950897 @ 19054753 (464.3M)  Linux swap

Block size=512, Number of Blocks=20005650
DeviceType=0x0, DeviceId=0x0

```

---

### Post by pxwpxw on 2007-07-05
That will be useful info. 
More about the X window quality, how does this picture look to you (it is not full screen, but good quality as seen here).
[http://img247.imageshack.us/img247/4176/tulips2er3.jpg]("http://img247.imageshack.us/img247/4176/tulips2er3.jpg")

Here is another ati version of xorg.conf with changes made to suit the later version iMacg3.
As for the fbdev version, I think it is just using the startup open firmware video setting, and needs to get that set befroe X windows starts up - not sure of the details. Try the ati.
 
======

---

### Post by youngwun0 on 2007-07-06
Nope, that gave me an error and wouldn't let me in the desktop, i changed all the parts that said ati back to the original writing and then it let me back in but nothing new, same results..... i pretty much give up i will have to wait until i can snatch up enought money to buy a new cd-rom slot to reinstall mac os x :(

---

### Post by pxwpxw on 2007-07-06
Is there any way you can get a copy of the log from running the ati?
Never mind, I have seen hardware problems with ati before, impossible to tell whether it is worth pursuing without the log.

Stay with the fbdev.

Without being there I am guessing, but it looks to me this is whats happening and where it might be fixed -

The poor quality you are getting is not shown here for your desktop screen shot, because that is the input to your  video display, not what you see on the screen, and i dont see it here displayed on my screen. You would need a photograph  to show me what you are seeing. 

I think you are looking for something to set the iMac video mode depth before X is started up so that it shows what it is being given, not a low color version. I have had to use low color settings here sometimes, and at 8 bit  colors, it is so limited you cant read some of the multicolor stuff on a menu.

There may be other ways to set the open firmware video before X starts up "fbdev", without having to reinstall Macos. 
(you can download and install via the net  from ubuntu mirrors)
```

 sudo apt-get install fbset

```
fbset is a utility of the same name as the package. It shows and changes video modes from the commnd console. 
I think nvvideo is another utility from earlier linux versiions, but I cant find it sofar, still looking.

I will post to this thread if I find anything usefull.

Meanwhile, you can always start into a command console using
```

boot: Linux single

```
and there are some other tricks and utilities that make debugging from the command console easier, including starting in the console then going to desktop manually.
If you have a usb stick there it is useful for saving info from the command console and transfer to another computer.
2 other good command line console utilities - 
```

 sudo apt-get mc gpm

```
gpm gives you a mouse cursor for copy and paste and mc is a text-graphic file manager, both for command console.
Then there is "tab completion" and history (using the up and down arrow keys).

---

### Post by youngwun0 on 2007-07-07
I'm sorry i'm still confused here..i installed fbset and i'm done now what shall i do ? not sure what to edit or do..

---

### Post by pxwpxw on 2007-07-07
First you read man fbset.
Then you just run fbset and it will list the current settings, it wont change anything
```

fbset

```
Here is what I get on the G5 with nvidia card (which doesn't work with fbdev).
```

admax@bigmac:~$ fbset

mode "1680x1050-53"
    # D: 100.000 MHz, H: 58.140 kHz, V: 53.339 Hz
    geometry 1680 1050 1680 1050 8
    timings 10000 16 16 16 16 8 8
    rgba 8/0,8/0,8/0,0/0
endmode

admax@bigmac:~$ fbset -i -v
Linux Frame Buffer Device Configuration Version 2.1 (23/06/1999)
(C) Copyright 1995-1999 by Geert Uytterhoeven

Opening frame buffer device `/dev/fb0'
Using current video mode from `/dev/fb0'

mode "1680x1050-53"
    # D: 100.000 MHz, H: 58.140 kHz, V: 53.339 Hz
    geometry 1680 1050 1680 1050 8
    timings 10000 16 16 16 16 8 8
    rgba 8/0,8/0,8/0,0/0
endmode

Getting further frame buffer information
Frame buffer device information:
    Name        : OFfb NVDA,Displ
    Address     : 0x98004000
    Size        : 2150400
    Type        : PACKED PIXELS
    Visual      : STATIC PSEUDOCOLOR
    XPanStep    : 0
    YPanStep    : 0
    YWrapStep   : 0
    LineLength  : 2048
    Accelerator : No
admax@bigmac:~$ 

```

Dont try to change anything, just observe. I still dont know exactly how to apply it. I have also found "nvvideo"
which is supposed to read or change the nvram settings for video in the mac openfirmware.
The other way it might be done is at the boot menu by adding settings for vmode=xx and cmode=yy
You do that at the startup "boot:" prompt. But I have to find the exact way that is done.
I  am still looking for the answer.
Not having an iMacg3 here to try things just makes it a bit more difficult for both of us.
Could do with a bit of help from  someone who has had the same problem.

---

### Post by youngwun0 on 2007-07-07
oh ok, well just for reference this s what i get when doing both commands in terminal:

```
jay@ubuntu:~$ fbset

mode "1024x768-116"
    # D: 100.000 MHz, H: 93.985 kHz, V: 116.318 Hz
    geometry 1024 768 1024 768 8
    timings 10000 16 16 16 16 8 8
    rgba 8/0,8/0,8/0,0/0
endmode

jay@ubuntu:~$ fbset -i -v
Linux Frame Buffer Device Configuration Version 2.1 (23/06/1999)
(C) Copyright 1995-1999 by Geert Uytterhoeven

Opening frame buffer device `/dev/fb0'
Using current video mode from `/dev/fb0'

mode "1024x768-116"
    # D: 100.000 MHz, H: 93.985 kHz, V: 116.318 Hz
    geometry 1024 768 1024 768 8
    timings 10000 16 16 16 16 8 8
    rgba 8/0,8/0,8/0,0/0
endmode

Getting further frame buffer information
Frame buffer device information:
    Name        : OFfb ATY,Rage12
    Address     : 0x96008000
    Size        : 786432
    Type        : PACKED PIXELS
    Visual      : PSEUDOCOLOR
    XPanStep    : 0
    YPanStep    : 0
    YWrapStep   : 0
    LineLength  : 1024
    Accelerator : No
jay@ubuntu:~$ 

```

---

### Post by pxwpxw on 2007-07-07
Thats very interesting. I'll sleep on it.

---

### Post by youngwun0 on 2007-07-07
Hey sorry to pester you but would you have any other ideas of using any other OS that would run fine (video and all) on a imac g3 with ubuntu installed on it already using maybe net installation methods rather then cd/dvd or firewire ? I am stuck here now and the screen is getting out o hand, i really do appreciate the help you have provided me with over the past week and a half and 8 pages so far, thanks alot... not quite sure what has happened and what can be done, i kinda wish i stood on mac os x until i got a way of restoring it in case this happened :(

---

### Post by pxwpxw on 2007-07-08
If you google "mac on linux" that will keep you busy while I get some thoughts together about the other issues.  I have tried a few things, and starting to think macosx will not solve the linux X windows problem, that may have only been the case for OldWorld macs, and I know that MacosX  10.4 has no affect on my iBookg4. More later, I hear what you say.

Later:

To get back to a simple xorg.conf that should work as well as any, with minimum fuss.
And to clear any corrupt settings from Mac Open Firmware.

1. from ubuntu, note down the open firmware boot-device setting for later use, if you need to restore it manually from open firmware.

```

 sudo nvsetenv boot-device

```

2. Then shut down and start up again holding down 4 keys Command(Apple)-Option-P-R until the second chime. That will reset open firmware to clear any wrong settings.

Then restart as usual. Go to 3.

========================
you should not need this part, but just in case, make a copy: 

If it does not restart as usual, try another restart with the Option key held down.

Or start into Open Firmware by 4 keys Command-Option-O-F held down at start up.
Then at the open firmware prompt
```

0> boot hd:,\\:tbxi
if that fails
0> boot xxxxxx
where xxxxxx is the boot-device you saved from above.

```
========================

3. In ubuntu, get to a console  using < Alt-F2 >, or from the boot menu using < boot: Linux sungle >

Make a new xorg.conf 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

at the first menu - Xserver Driver - choose fbdev
at the second menu - Video Modes - choose only one - 1024x768
finish.

That should rename and rewrite /etc/X11/xorg.conf for 1024x768 depth 24 . Should work as well as any.
  
Restart or exit from Linux single to try it. 

I found a problem here with multiple display resolution setings, when using fbdev. And dpkg-reconfigure does the job with no editing. But be sure to choose only one resolution. 
 
I hope that works.

---

### Post by youngwun0 on 2007-07-08
Nope, followed all the instructons very carefully and well, nothing has changed but the font size, the mouse curcor still moves to the edges and the color is still very grey in 24 bit , i don't think i have that kind of luck, i think i should move foward as i do not want to waste your time any further you have been very very helpful and i have learned alot from this experience, i shall stick with loading ubuntu on pc's or on newer macs

---

### Post by Oliver Barker on 2007-07-08
you mght have done this but in 10.4 you go into disk utility (apps - utilities - disk utility) then with the blank CD installed click on it then burn and burn the .ISO image to it hen try booting off it then hen you hear the noise hold hold down alt then select the CD.

Soz if its been mentioned but i didn't have time to read all the pages!

---

### Post by youngwun0 on 2007-07-08
> **Oliver Barker said:**
> you mght have done this but in 10.4 you go into disk utility (apps - utilities - disk utility) then with the blank CD installed click on it then burn and burn the .ISO image to it hen try booting off it then hen you hear the noise hold hold down alt then select the CD.

Soz if its been mentioned but i didn't have time to read all the pages!

Yup, that is one of the methods i used before installing ubuntu as well as holding c down at startup, clicking the setup.app and restarting, holding the apple, alt and o+f buttons or whatnot ect.... i read on the ubuntu wiki that when such cd's do not boot it is likely that the cd-drive is very old and will not boot cd's, doesn't have a solution so my guess is i have to replace it which i have not the money for at the moment.

---

### Post by youngwun0 on 2007-07-09
Hey pxwpxw,

I have a question for you kinda un-related to this whole video monitor ordeal, anyway i have been customizing my panels on ubuntu top and bottom... moved the clock, firefox icon, taskbar ect,,, problem is i don't like the look anymore and it's starting to looks messy, any idea how i can get everything back to the default style and way ? Also i use GAIM instant messenger for msn and when i X/Close the box it quits the entire program, i don't remember it always doing that anyway to allow it to stay open unless i choose quit ?

Thanks bro

---

### Post by pxwpxw on 2007-07-09
> **youngwun0 said:**
> Nope, followed all the instructons very carefully and well, nothing has changed but the font size, the mouse curcor still moves to the edges and the color is still very grey in 24 bit , i don't think i have that kind of luck, i think i should move foward as i do not want to waste your time any further you have been very very helpful and i have learned alot from this experience, i shall stick with loading ubuntu on pc's or on newer macs
Yep, I give up, but sure it must be something simple. Maybe Gamma - see attachment.

---

### Post by pxwpxw on 2007-07-09
Panels and past sessions and other desktop config stuff are in .hidden folders in your home directory, like ~/.config for my xfce4, you may have to delete something to trigger a fresh start. But you should go to the Desktop forums and another thread for details, this thread is about worn out and off topic by now (but all interesting to me). Know 0 about GAIM, must do some sometime.
If you want to put a network installer or rescue on a usb stick (bootable) start a new topic for that one, its feasible.
Good luck.:)

---

### Post by youngwun0 on 2007-07-09
Thanks bro, i really appricate all the help... if ever i fix this or whatever i wil update you on it i'll let the thread rot and just enjoy ubuntu with the video selection i have now :)

---

### Post by pxwpxw on 2007-07-09
I don't know if you saw my 2nd last post - you should try adlusting colour balance, that color utility should be in ubuntu desktop. Might make your CRT display colors look better.

---

### Post by youngwun0 on 2007-07-09
Call me stupid but where can i find this utility ?

---

### Post by pxwpxw on 2007-07-10
> **youngwun0 said:**
> Call me stupid but where can i find this utility ?

I looked in a debian-gnome desktop, I can't find it either, but it is in xubuntu Display Preferences - Gamma correction.
 It  lets you experiment with changing the R G B colour levels, and set them how you want, or revert to "as installed". If your problem is with color balance, it might be useful.

The Display Preferences panel is in the Xfce Settings Manager (/usr/bin/xfce-setting-show) which is part of the xfce4 desktop manager meta package. This comes with xubuntu-desktop or it can be installed after the ubuntu-desktop with synaptic (search for xfce4) or apt-get. I think  you need  universe  multiverse in your /etc/apt/sources.list 
```

 sudo apt-get install xfce4

```
This will also give you an xfce session as an interesting more compact alternative to the gnome desktop, just choose beween gnome and xfce at the gdm login. Should not take more than a few hundred MBytes disk space, it uses some of the same libraries and stuff as the gnome desktop you already have (in ubuntu-desktop). I am not sure if you would gain anything by installing the full xubuntu-desktop.

---

### Post by youngwun0 on 2007-07-13
I have an odd question but idk just figured i'd ask, do you think i could reinstall or install xubuntu or and maybe something will change or fix ? If so any idea how would i go about doing so wthout the cd and having ubuntu already installed ?

---

### Post by pxwpxw on 2007-07-13
If you just install xfce4 (see above), that is the xubuntu desktop, maybe not quite so complete but it is what xubuntu-desktop uses. Then run a xfce session from the gui login chooser.
For a complete reinstall, you would have to put installer images on a usb stick (similar to your install from macosx) or do a netboot from another computer, linux system preferably. I have not done net booting, a bit tricky, you would need to read about it.

---

### Post by youngwun0 on 2007-07-14
At this point i am desprete, i would love to install something that works perfectly... mac os 9, mac os x or linux of any kind but al i have is internet and usb... i havent a clue how to boot anything from usb :(

---

### Post by pxwpxw on 2007-07-14
```

 sudo apt-get update
 sudo apt-get install xfce4

```
That will install from the internet. You might have to comment out  "# deb cdrom:... " entries in /etc/apt/sources.list if it complains. 
You can install any ubuntu packages if you have an internet connection.
I can show you how to boot yaboot/linux install  from usb, but I dont know any way to do it with macosx, unless you can find a firewire CD drive - macosx is bootable from firewire CD drive,

---

### Post by youngwun0 on 2007-07-15
hey bro i have 1 more question kind of off-topic but still there, i think i can deal with the color i won't bother to reinstall or anything until i get some cash, i just got a desktop pc that's pretty nice so hopefully i can get that running with ubuntu :D anyway, on my mac ubuntu install i think i deleted my root username (not the root itself) i had which was "jay" i created another one with all admin privileges but for some reason when i log into the new one the volume won't fix, there are no admin privileges and i cannot edit accounts or anything as if i were a guest or something.... anyway to set myself as root using the command console or something ? there are only this username and root but as you may already know root cannot log into the desktop :( 

thanks deeply for all the help you have brought this far i really appreciate it

---

### Post by youngwun0 on 2007-07-15
My usb devices will also not show such as my ipod and psp which have worked fine before, my mouse and keyboard are usb and work fine but anything memory related with usb wont read, it does not show on the desktop or anything or in file browser :(

---

### Post by pxwpxw on 2007-07-15
If I understand correctly what happened you need to do this:

restart
 
boot: Linux single

```
# usermod --append --groups admin jay2
```

Should give sudoer status to jay2 (or whatever your new username), but the UID will not be the same as the old one. So any surviving files belonging to the old UID may not be accessible, but dont fiddle with UID until you know what you are doing. See man usermod and man ls.

---

### Post by youngwun0 on 2007-07-15
Just tried booting from linux single but when it is supposed to go to the desktop part it freezes with a black screen :(

---

### Post by pxwpxw on 2007-07-16
At the boot: prompt press <tab> to see the list of options.
"Linux" is normally the name, it might be something else. It is case sensitive.
You dont get a desktop, you get a root console.

---

### Post by youngwun0 on 2007-07-16
Ok when i pressed tab at the yaboot area where it says "Boot:" it said "Linux" and a huge gap area that said "old" i typed Linux as well as Linux old and it took me to the desktop login area no root console....

---

### Post by pxwpxw on 2007-07-16
Nearly there,

You type 
 
   Linux single

or maybe its Linux Single

---

### Post by youngwun0 on 2007-07-16
Neither command works, Linux single brings me to a blank black froozen screen and Linux Single bring me to the desktop login, no command console... i type ALT+F2 but when i login and enter that command you gave it gives me a list of option commands like a-append and stuff like that....

---

### Post by radicalspud on 2007-07-16
in my experience with G3 Powerbooks and burned CDs, i've concluded that the only way they will reliably read CDs is if they are burned at 4x speed or less. sometimes you can get away with 8x, but i usually don't try that because i got tired of wasting them. i had the most trouble with getting them to boot (i.e. sometimes they will read but not boot).

i know the Powerbook CD-ROM drives were pretty crappy...i'm not sure about the ones in iMacs, but they are basically laptop drives, so i'm guessing you have one with very similar if not the same internal mechanism as those in G3 (bronze/Lombard) powerbooks. these machines are definitely relics now, and apple seemed to try to cut costs wherever they could with them. they will run forever (i have 2 of these powerbooks and they both work great, albeit a little slow), but some of the components aren't really up-to-snuff with their PC counterparts.

so, if you're willing to take another shot, try burning the Ubuntu PPC installer disc at 4x or even 2x (which will take awhile) and then try to boot from it again.

:guitar:

---

### Post by youngwun0 on 2007-07-16
Thanks radicalspud i think i will try that as soon as i get cd's, i tried multiple times on a cd-rw burned at 4x and 10x then i tried at 48 or 52x on a regular cd-r maybe, just maybe that is the problem as this is not the first time i have read that, thanks for the advice again :)

---

### Post by pxwpxw on 2007-07-18
> **youngwun0 said:**
> Neither command works, Linux single brings me to a blank black froozen screen and Linux Single bring me to the desktop login, no command console... i type ALT+F2 but when i login and enter that command you gave it gives me a list of option commands like a-append and stuff like that....

OK, there is something wrong there, I will recheck it all here and do it again.
Hang in there.

---

### Post by ubanchaos on 2007-07-18
did u burn the iso to a data CD if u didnt u need to download a isoburner

---

### Post by pxwpxw on 2007-07-18
> **youngwun0 said:**
> Neither command works, Linux single brings me to a blank black froozen screen and Linux Single bring me to the desktop login, no command console... i type ALT+F2 but when i login and enter that command you gave it gives me a list of option commands like a-append and stuff like that....

Catch 22. To run this you need to be root or a sudoer, but you need to run this to be a sudoer.

Any of these 3 are OK.
```
admax@bigmac:~$ sudo usermod -append --groups admin testuser
admax@bigmac:~$ sudo usermod -a --groups admin testuser
admax@bigmac:~$ sudo usermod -a -G admin testuser

```
But this doesn't work:
```
admax@bigmac:~$ sudo usermod --append -G admin testuser
Usage: usermod [options] LOGIN
```

Tested in:
```
admax@bigmac:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
```

---

### Post by pxwpxw on 2007-07-18
> **youngwun0 said:**
> Neither command works, Linux single brings me to a blank black froozen screen and Linux Single bring me to the desktop login, no command console... i type ALT+F2 but when i login and enter that command you gave it gives me a list of option commands like a-append and stuff like that....

**Linux single**

Please see  my posts above as well.

If your yaboot boot: menu option is Linux either of these work as tested here
```
 
 Linux single

 Linux S

```

 Nothing else will work.

But if still not working please post text from 
```

 cat /etc/yaboot.conf

```
It might have been corrupted. I can't think of any other reason for failure to get a root console.
If you can become root any other way then this is not so much a problem.

If it looks like  a screen problem at the console then try
```
Linux S video=ofonly
```

(I need to check that one here)

---

### Post by youngwun0 on 2007-07-18
This is my yaboot file:

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash video=ofonly"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash video=ofonly"
```

---

### Post by pxwpxw on 2007-07-18
That is in good order, no problem there. What now?

---

### Post by youngwun0 on 2007-07-18
Yup, problem... none of these commands you gave ive me a root console it will only load either the desktop or a blank black screen, tried various boot commands to.... i can always login as root in the command console while in desktop or before logging in the desktop but when i run the command you gave me i just get a list of commands that like a-append/ --append ect..... it doesn't run the command you gave...

---

### Post by pxwpxw on 2007-07-18
If you can get in as root somewhere then I am not sure what problem we are still trying to fix?
 I don't understand why it wont let you do Linux single, but maybe that does not matter?
An alternative way of re-instating a sudoer, if you are root
```

visudo

```
Then you add a line giving your new username the same priveleges as root

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Might be wise to cosult the manual first.

---

### Post by youngwun0 on 2007-07-19
Ok so i entered visudo as root in the command console, it opened up a file called /etc/sudoers.tmp or something like that, i edited below the line "root ALL=(ALL) ALL" and added "jay2 ALL=(ALL) ALL" with jay2 being my username... i did the same thing here with "%admin ALL=(ALL) ALL" and added jay2 in the place of admin below that line as well... i restarted my mac and came back but still no usb mounting, no volume control, no add/remove programs, no user editing ect... I am having just about the worst luck with ubuntu and my mac :( nothing seems to go my way.

---

### Post by pxwpxw on 2007-07-19
I think you need to get some other inputs, time to take this one to the General Help forum, its not Applemac specific its about permissions and groups and Linux single.

Same goes for the Video problem, the Multimedia & Video forum will probably produce more useful inputs. Again its about the video driver and X windows, not particularly Applemac.

---

### Post by youngwun0 on 2007-07-19
will do bro, once again thanks alot for the help i will see what i can learn and do on my own and if not i will post a new thread in the proper section as this thread has gone far too long anyways hehe thanks again for all the help it's good to know there are people like you who like to help and have no problems with it, only 2 people besides you posted so that says alot, i appreciate it :)

P.S. Don't worry i'm not blaming ubuntu or the applemac, just saying that i have had some bad luck with this so far i'm sure it happens to 1/10 people are rarely, ubuntu seems awesome and that's why i dont mind sticking by it :D

---

### Post by gvigorus on 2007-07-25
> **youngwun0 said:**
> hey bro, I just finished installing it BUT for some reason after installation and restarting it loads and starts everything but stops at "running local boot scrict" I can press enter and log in but all i get is a command terminal or something :( anyway to fix this or get into the ubuntu desktop ?
Youngwum, i'm having the same issue on Lombard with 400Mhz and 512 RAM. CD burned and tested MD5, yet my Powerbook G3 does not boot from the disk. I tried doing what you described and per manual about downloading those four files into OS X root folder, then calling Yaboot from Open Firmware. Still no luck, i get exactly the same message that the file or volume is corrupt and nothing happens. How did you get yours to boot? Can you please show the steps you took? 
Thanks a lot, really hoping to get this issue sorted out, it's super frustrating.

---

### Post by pxwpxw on 2007-07-26
> **gvigorus said:**
> Youngwum, i'm having the same issue on Lombard with 400Mhz and 512 RAM. CD burned and tested MD5, yet my Powerbook G3 does not boot from the disk. I tried doing what you described and per manual about downloading those four files into OS X root folder, then calling Yaboot from Open Firmware. Still no luck, i get exactly the same message that the file or volume is corrupt and nothing happens. How did you get yours to boot? Can you please show the steps you took? 
Thanks a lot, really hoping to get this issue sorted out, it's super frustrating.

You may have got the CD installer image files - there are 3 sets hd-media, netboot, cdrom.
See [http://ubuntuforums.org/showthread.php?t=390770](http://ubuntuforums.org/showthread.php?t=390770) **(Post  #4**)
You also need an iso with the hd-media set.

---

### Post by ajmctaggart on 2007-07-26
WELL IT SEEMS YOU'RE ON YOU'RE WAY...but here's something for everyone else in here...

you may already know this but...

Is it common knowledge to everyone already that in Disk Utility in OS X you need to convert your .iso to a cd/dvd master (.cdr)?  I only ask because it's amazing how many installation disks will fail when you don't burn them so they can boot...

Just a thought...this may not be a prob for anyone else, but I didn't know this for a long time...

---


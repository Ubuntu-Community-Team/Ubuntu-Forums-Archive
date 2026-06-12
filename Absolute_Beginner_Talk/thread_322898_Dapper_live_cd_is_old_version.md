---
title: "Dapper live cd is old version???"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-12-21
[I]Hi everyone, I've just tried to re-install dapper with the same live cd that has worked perfectly twice before but now it stops mid way thru and tells me > failed to start X server
and that I should > check my version
Interestingly I ve found that the versions given in this error message are that I'm running > X version 11, revision 0, release 7.0 and the wiki.x.org site has release 7.1 as the latest. It also has patches available for release 7.0 but I've no idea how to stick them into my system.
that aside, what seems more interesting to me is the same message has me using kernel version 2.6.15-26-386 and yet my splash screen and synaptic both agree that I'm running version 2.6.15-27-386
What the heck?? Is this just a minor glitch in the error message?[/I]

befuddled:confused:

---

### Post by 23meg on 2006-12-21
Do you get this error when booting with the live CD; I mean, can you not start X at all? Can you quote the exact message?
>  and the wiki.x.org site has release 7.1 as the latest. It also has patches available for release 7.0 but I've no idea how to stick them into my system.
Dapper uses Xorg 7.0, and the latest stable is 7.1, which is used by Edgy, the latest stable Ubuntu version. 
> that aside, what seems more interesting to me is the same message has me using kernel version 2.6.15-26-386 and yet my splash screen and synaptic both agree that I'm running version 2.6.15-27-386
What the heck?? Is this just a minor glitch in the error message?How do you get to Synaptic if you can't boot with the CD? Again, quoting the exact error message would be helpful.

---

### Post by carloslosgrande on 2006-12-21
Hi 23meg, Yeah this is related to reinstalling from the live cd. It won't do it, but I'm able to shutdown by power off, and then do a normal start up.
I stuffed up some things and I've not been able to fix them so I thought I'd just re-install, its good practice for me as there's so much I need to learn.
I can't give you the entire message as I only wrote down the things that seemed relevant.
When you ask if I can start X server, isn't that what the  message is saying can't be done or is there a workaround? This error basically stops the setup process and leaves no options other power off.

Sorry, I don't have more info.:(

---

### Post by az on 2006-12-21
> **carloslosgrande said:**
> Hi 23meg, Yeah this is related to reinstalling from the live cd. It won't do it, but I'm able to shutdown by power off, and then do a normal start up.:(

You can't boot the live cd anymore or you can't boot your newly reinstalled system?

In the case of the former, the list is pretty short - either your cd is scratched or you have hardware problems.  If it's the latter, did you wipe the partition or did you keep the existing data on the partition?

You can't reinstall on a partition without wiping the data.

---

### Post by carloslosgrande on 2006-12-21
Hi Azz, sorry I'm still not clear. I'm using the Live CD which first loads Ubuntu and then gives the option for install, but it doesn't get that far.

This problem occurs in the initial load sequence. I haven't got to the stage of deleting all the data, so I'm still able to get back into the system as its currently on the disc.
What I'm trying to do is re-install, delete the data, etc, etc.

The disc looks fine and has worked really well twice before. It seems to read it just fine except that it finds a discrepancy between the X version it finds and what it expects. and also between the Ubuntu version it finds and what **I** expect
This is what has me puzzled.

If its just the disc then I can easily reburn another but I didn't think that was the problem.

Thanks for any help

Carl:)

---

### Post by az on 2006-12-21
> **carloslosgrande said:**
> Hi Azz, sorry I'm still not clear. I'm using the Live CD which first loads Ubuntu and then gives the option for install, but it doesn't get that far.

This problem occurs in the initial load sequence. 

So, you are saying that the live cd does not boot anymore?



> **carloslosgrande said:**
> 

The disc looks fine and has worked really well twice before. It seems to read it just fine except that it finds a discrepancy between the X version it finds and what it expects. and also between the Ubuntu version it finds and what **I** expect
This is what has me puzzled.



If we are talking about booting the live cd, well, the live cd is read-only.  There is no way that it can try to use a different version of the X server.  In fact, if you booted from it once and it worked, there is no reason why you should no longer be able to boot it (unless you changed your hardware to something which uncovers a bug - which is highly unlikely since millions of people have successfully used that cd)

---

### Post by carloslosgrande on 2006-12-22
Hi Azz, yes it we're talking about booting from the live cd, it begins to boot up, setting up the various programs needed then it blanks the screen and then gives me the errors mentioned previously.

> If we are talking about booting the live cd, well, the live cd is read-only. There is no way that it can try to use a different version of the X server. In fact, if you booted from it once and it worked, there is no reason why you should no longer be able to boot it (unless you changed your hardware to something which uncovers a bug - which is highly unlikely since millions of people have successfully used that cd)
Exactly!

If I've changed my hardware then it happened without my knowledge!
I've booted from this cd twice and copied for a friend who has used it on his without any problems.
If I completely stuff my current version of Ubuntu I want to be able to reinstall from my live cd and that is my ultimate backup (I have my files etc backed up on a usb plug-in hdrive). I'm sort of counting on this so I'm concerned that it isn't working.
obviously I've [once again] done something but this time I'm completely unaware of it might be!
I have been having trouble with firestarter but only the module on the screen. It still shows as starting and stopping on the initial and final screens.:confused:

Ok, more info. Firestarter isn't starting up at all! it flashes past really fast but its definitely a 'failed' notice.

I've burned another copy of the LiveCD and tested it - seemed to work fine.
Tried to setup from said disc and got the same error message which I've copied;
> failed to start the X server (your graphical interface), It is likely that it is not set up correctly.
Would you like to view the X server output to diagnose the problem?  <yes>
then
> X Window System Version 7.0.0 Release date: 21 december 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux Ubuntu 2.6.15-26-386 #1 Preempt Thu Aug 3 02:52:00 UTC 2006 i686
Build date 16 March 2006
          Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version.

Module loader present
    Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown
   (==) log file: '/var/log/Xorg.0.log'
Time: Sat Dec 23 15:05:04 2006
   (==) Using config file: '/etc/X11/xorg.conf

detailed X Server output is exactly the same info. final page is

> the X Server is now disabled.
Restart GDM when it is configured correctly.

I hope this makes it clear to you or somebody

---

### Post by carloslosgrande on 2006-12-23
[I]Ok, Now I think there is something seriously wrong. I have an Edgy live CD which i just ran a check on with NO md5sum errors but starting the load prior to install I got the exact same error. ie > X Server failed to start:-k 
I think this may have something to do with firestarter not running - Its possible that someone got thru? Could a corrupt firestarter do this?
I don't know how to fix this.
If I uninstall Ubuntu ( fix mbr, then with GParted - delete the partition) - is it possible that the Live CD will then be able to restart X??:confused: 
Thanks in advance[/I]:-k

---

### Post by az on 2006-12-23
> **carloslosgrande said:**
> [I]Ok, Now I think there is something seriously wrong. I have an Edgy live CD which i just ran a check on with NO md5sum errors but starting the load prior to install I got the exact same error. ie :-k 
If you get that error while booting the live cd, and the cd is okay, you have hardware problems.  Try running memtest86 for kicks.  other culprits can be your optical drive or your video card.  

Are all your fans working?

> **carloslosgrande said:**
> 
I think this may have something to do with firestarter not running

No.  Not at all relevant.

> **carloslosgrande said:**
> 
 - Its possible that someone got thru? Could a corrupt firestarter do this?
I don't know how to fix this.
If I uninstall Ubuntu ( fix mbr, then with GParted - delete the partition) - is it possible that the Live CD will then be able to restart X??:confused: 
Thanks in advance[/I]:-k

Booting off a live cd has nothing to do with what is installed on your disk.

And you don't need a firewall unless you run a server - nothing listens to the outside world.

---

### Post by Sef on 2006-12-23
Since it worked before and not now, I am wondering if something happened to your graphics card.  Either it came a bit loose, or has gone bad (i.e. doesn't work right) or maybe something else.

Could you please post your computer specs, including your graphics card.

Might check that nothing has come loose inside the case.

---

### Post by carloslosgrande on 2006-12-23
Hello Sef, first up some details I have a Dell 5150 desktop, 160gb.

further details
internals; Intel EM64T
	Pentium 4 (0.09) 2993 MHz
	1st Cache; 16k 20927 Mb/s
	2nd Cache; 2048k 16264 Mb/s
	Memory; 510M 2597 Mb/s
	Chipset; Intel: 945p/g (ECC = dsiabled) – fsb; 199 MHz – DDR-II
settings; RAM: 265 MHz (DDR530) / CAS; 4-4-4-12 / dual channel (interleaved)
main drive; windows NTFS 149.01 GiB,  name; WDC WD1600JS-75NCB1 (ATA)

Graphics card is ATI Radeon X600.

I'm wondering about the graphics card, if it was loose or something wrong would I be able to play Videos? Because I can.
I had a look in the back of the box but honestly if I tripped over a graphics card I wouldn't recognise it.
There's nothing obvious hanging loose or looking out of place.
Is there some simple test to check if its the card? Other than looking.

thanks.

---

### Post by carloslosgrande on 2006-12-23
Hi Azz and Sef.

I don't run a server, the fan seems to be working - I could see it spinning, and if the optical drive was dicky then I probably couldn't play DVD's but I can.
Now I'm going to try the memtest86+
Thanks guys

---

### Post by carloslosgrande on 2006-12-24
Ok, my Computer details are already listed above and here is the output from Xorg.conf (I hope)
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
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL E196FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
        Monitor         "DELL E196FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720 x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720 x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720 x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720 x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720 x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720 x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

I've also run the Memtest86+ without any errors, ran it for 10 hours last night.
Is it possible that I could have inadvertently caused this? I haven't been playing around with  the terminal like I did last time so I'm quite surprised that this error has arisen.
I'm stumbling in the dark here, so any ray of light is welcome.

---

### Post by carloslosgrande on 2006-12-31
OK, since this last post I've had to reinstall again n again. After your advice re the hardware (Sef n Azz) I got down into the guts of the thing and vacuumed out all the dust and gently tried the cards to see if any seemed loose. Nothing noticed, but the very next attempt to reinstall (from 'safe graphics mode') worked just fine - the Dapper release. The Edgy release still won't go, but that doesn't really matter as its Dapper I'm interested in.
THEN, I got this message > failed to start the X server (your graphical interface), It is likely that it is not set up correctly. again
on my normal start up (ie not on live cd)!! so I reinstalled again.
After this I ran GParted to resize and got tooooooo blase and careless and zapped everything! So my long dithering with removing XP has been pushed ahead.
*_Now I have only Ubuntu but I'm still concerned that this X Server error is not corrected._*
Of course all this happened just as the 'Quake hit Taiwan and knocked out all net connetions - so no easyubuntu or forums!! panic stations!
If anyone has any idea what's behind this I'd be really appreciative.
Carlos.

---


---
title: "Gunze USB Touch Screen monitor"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by PhillD on 2007-03-12
Hi All,

I have been trying for the past week to install a Planar (Gunze) touch screen monitor on xubuntu 6.10.  I have trawled the forums, searched the search engines and sucked up every piece of information I can find (even made some progress!) but I am now stuck.  To make the situation worse, I am completely new to Linux so I have no idea what I’m doing or most of the terminology that is used in these forums (kernel headers etc..)

Here’s what I do know.

The touch screen monitor is made by Gunze
There is a driver for monitor in Linux called Gunzets
The drivers is not available as a package through ubuntu
The drivers were last updated 3 years ago
The drivers were written for Xfree86 (Xfree86 is the version of the X server for those of you who are new like me and didn’t understand this for the first 30 hrs of woking on this problem), (Xubuntu does not operate on Xfree86 it works on Xorg).
I am trying to connect the monitor via USB
It’s not working

By reading the forums I learned that lsusb would show me a list of connected USB devices…..I am almost 100% certain that the monitor is being detected (sorry for the lack of actual data).  Both the keyboard and mouse I used are USB and are listed with device numbers and names (Dell- (This is correct)).  There is a third entry (further down the list) with numbers but no detected device name.  I have no other USB devices connected.

I followed the instruction manual for gunzets only to stumble on the first step:
“In order to use the touch screen in X, you should install in your system the ‘xf86Gunze’ module, part of this distribution.”
Upon looking at the files contained in the gunzets folder there were 2 files named xf86Gunze.

A:	xf86Gunze.so
B	xf86Gunze.c

Ok, so even if I knew which file to choose (which I don’t) I do not know how to install it or even if can be installed under the Xorg X server.

Any attempt to run any of the other files yields instant error messages that the file or folder does not exist.  I am also using the sudo command for all of the execute commands. 

So ignoring the fact I failed on step 1 I went onto step 2 to see if I could go further.

The instruction manual tells me that “The compiled module (‘xf86Gunze.so’ for Xfree86 3.3 or ‘gunze_drv.o’ for XFree 4.0 should go in the module directory of your X server, usually ‘/usr/X11R6/lib/modules’ for XFree 3.3 or ‘usr/X11R6/lib/modules/input for XFree86 4.0.  When the file is in place a proper ‘XF86Config’ will arrange for its loading”  before I write anything else, just imagine how complicated that is for a newbie especially when none of those folders exist on my system.  Despite the confusion, I worked out that the correct folder was usr/lib/xorg/modules/input and the correct configuration file was /etc/X11R6/xorg.conf

The next few pages of the manual go on to explain what you need to add to the config file mentioned above.  These were added but no surprise, when I restated xubuntu, the touch screen was not working.  After checking the log files located in /var/logfiles/xorg.0.log (something like that (more stuff I learned off the forum).  It said that it could not locate the module ‘gunzets’ which is not surprising considering its not really installed……

Anyway as you can tell by the mess I am making of my first post, I really don’t know what I’m doing and any help would be greatly appreciated……I know your all going to ask me to post data and specific error messages and I will be able to do this tomorrow (I could not connect to the Linux box via file sharing from my domain controlled computer, so I’m going to have to mess with that tomorrow).  I was just hoping that some brilliant person/average Linux user could give me some hints to what I am doing wrong or someone might actually know the answer to this problem.

On a side note:  I am really trying to give Linux a try but man is it hard, it’s not that it’s different it just really is complicated.  I think very much like a windows user and where hardware you have just works (via double clicking an EXE file).  There is some good documentation out there on what Linux is but not how it works!  E.g. Windows files execute from an EXE file, Linux files execute from a ???? file.  This is stuff new users need to know as not all the software people need to install is available in the repositories.

Anyway, they are shutting off the lights, I have to go (sorry for the long post)  I will add more tomorrow.

Phill D

---

### Post by PhillD on 2007-03-13
Hi again,

I have actually made some progress on this issue but it’s still not working.  I’ll update you on where I’m at and post the technical information I left out yesterday.

First of all I think I may be over reading the instruction manual ([http://ar.linux.it/software/gunzets/)](http://ar.linux.it/software/gunzets/)).  Because I am so new to linux (a week old) I am making an assumption that everything that is written in this manual is a step I have to take.  E.g. first few lines of the manual………..

[COLOR="black"][FONT="Times New Roman"]“In order to use the touch screen in X, you should install in your system the "xf86Gunze" module, part of this distribution. 

The compiled module (xf86Gunze.so for XFree86 3.3 or gunze_drv.o for XFree86 4.0) should go in the module directory of your X server, usually /usr/X11R6/lib/modules for XFree86 3.3 or /usr/X11R6/lib/modules/input for XFree86 4.0. When the file is in place, a proper XF86Config will arrange for its loading.”[/FONT][/COLOR]

Is this 1 instruction or 2? Do I have to run some kind of install and then copy over the appropriate module to the specified directory?  Or does this just mean by copying the module to the specified directory you have satisfied the statement in the first sentence.

The second step (or third depending on how you interpret the previous instruction(s)) is to make changes to the XF86Config file as specified in the manual.  As there is no such file (because ubuntu uses the Xorg X server and not XFree86) I added this information to my xorg.conf file

[FONT="Courier New"]Section "InputDevice"
	Identifier	"TouchScreen"
	Driver		"gunze"
	Option		"Device"	"/dev/gunzets"
	Option		"BaudRate"	"9600"
	Option		"Smoothness"	"9"
	Option		"TappingDelay"	"0"
	Option		"JitterDelay"	"50"
	Option		"DebugLevel"	"0"
	Option		"Res12Bit"	"False"
	Option		"SendCoreEvents" "yes"
EndSection[/FONT]

Under the “ServerLayout” section I added:

	[FONT="Courier New"]InputDevice	"TouchScreen"[/FONT]

The thing which has really surprised me here is that by adding the gunze_drv.o file to my /usr/lib/xorg/modules/input/ folder, when the system boots up, the Driver "gunze" is actually detected and loaded.  THIS IS THE PROGRESS I HAVE MADE.  Slow I know but I’m much further than I was a week ago.

I don’t know if this is the real reason the driver is detected or  just a consequence of the failed make command I have been running (error shown later).

Even though the driver is detected the touch screen still does not work.  Here is the output of the Xorg.0.log file.  (Please note, I have trimmed this down considerably for items relavant to the touch screen.  I will post the full log on request.


[FONT="Courier New"]X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
(**) |-->Input Device "TouchScreen"
(II) LoadModule: "gunze"
(II) Loading /usr/lib/xorg/modules/input/gunze_drv.o
(II) Module gunze: vendor="Alessandro Rubini and Gunze USA"
	compiled for 4.0.3, module version = 1.4.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.1
(**) TouchScreen: always reports core events
(**) Option "Smoothness" "9"
(**) Option "JitterDelay" "50"
(**) Option "TappingDelay" "0"
(**) Option "DebugLevel" "0"
(**) Option "Res12bit" "False"
(II) XINPUT: Adding extended input device "TouchScreen" (type: Gunze Touch Screen)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };

xf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directory(II) Configured Mouse: ps2EnableDataReporting: succeeded
xf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryCould not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
xf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directoryxf86Gunze: Calibration data absent or invalid, using defaults
/dev/gunzets: No such file or directory[/FONT]

THE LOG ENDS HERE, I DID NOT REMOVE ANYTHING AFTER THIS LINE

So the driver is loaded but it cannot detect the device?  This is not a problem as I am connecting via USB and the manual says I have to perform additional steps as follows:

[FONT="Times New Roman"]“This [usb]driver has been developed and tested with Linux-2.4.0 and works with Linux-2.2.18 as well. 
Input data is made available through an entry point in /dev (using devfs if available) (FIXME: devfs support is not yet implemented) or through the input engine (the input.o module) (FIXME: input support is not yet implemented). By default it uses its own /dev entry point, dynamically allocated from the misc device driver.
 
Quick Start

If all of your modules are in place, you can just invoke 
make
./gunzets_load
and read the section about X support, above. 
If you want to use the input mechanism (currently unimplemented), add use_input=1 to the gunzets_load command line.
Compiling and loading
In order to successfully load the module you need to have the following facilities compiled in your kernel or loaded as modules: 
•	usb generic support (usbcore.o) 
•	a usb host controller driver (usb-ohci.o o usb-uhci.o) 
•	support for misc devices like the ps2 mouse (misc.o) 
•	the input mechanism (input.o) 

To compile the driver just make. If your 2.4 or 2.2 kernel headers are not available from /usr/src/linux/include then specify KERNELDIR to point to your kernel source directory, either on the make command line or in the environment. For example: 
make KERNELDIR=/usr/src/linux-2.4
To load the driver, use insmod: 
insmod ./gunzets.o
To use the input mechanism, specify it on the command line: 
insmod ./gunzets.o use_input=1
To automatically create the entry point in /dev (needed if you are not using the input mechanism) run the gunzets_load script instead: 
./gunzets_load
“[/FONT]

So now I’m confused again, do I quick load or do I compile?  Whats the difference?

I tried to do the make using the following command due to the Kernel difference

[FONT="Courier New"]sudo make KERNELDIR=/usr/src/linux-headers-2.6.17-10-generic[/FONT]

and I got the following error

[FONT="Courier New"]cc -Wall -O3 -fomit-frame-pointer -I/usr/src/linux-headers-2.6.17-10-generic/include   -c -o gunzets.o gunzets.c
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/asm/thread_info.h:16,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/capability.h:45,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/sched.h:44,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/module.h:9,
                 from gunzets.c:28:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/processor.h:76: error: â€˜CONFIG_X86_L1_CACHE_SHIFTâ€™ undeclared here (not in a function)
/usr/src/linux-headers-2.6.17-10-generic/include/asm/processor.h:76: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/sched.h:49,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/module.h:9,
                 from gunzets.c:28:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:254:46: error: division by zero in #if
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/sched.h:49,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/module.h:9,
                 from gunzets.c:28:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜jiffies_to_msecsâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:259: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:259: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:259: error: for each function it appears in.)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:265:46: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜jiffies_to_usecsâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:270: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:278:46: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜msecs_to_jiffiesâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:283: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:291:46: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜usecs_to_jiffiesâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:296: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜timespec_to_jiffiesâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:315: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:321: error: â€˜SHIFT_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜jiffies_to_timespecâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:334: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜timeval_to_jiffiesâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:356: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:360: error: â€˜SHIFT_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜jiffies_to_timevalâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:372: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜jiffies_to_clock_tâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:386: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜clock_t_to_jiffiesâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:397: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h: In function â€˜jiffies_64_to_clock_tâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/jiffies.h:417: error: â€˜CONFIG_HZâ€™ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/rwsem.h:26,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h:42,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/sched.h:57,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/module.h:9,
                 from gunzets.c:28:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h: In function â€˜__down_readâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h:105: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h: In function â€˜__down_writeâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h:157: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h: In function â€˜__up_readâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h:194: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h:188: warning: unused variable â€˜tmpâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h: In function â€˜__up_writeâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h:220: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h: In function â€˜__downgrade_writeâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/rwsem.h:245: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/sched.h:57,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/module.h:9,
                 from gunzets.c:28:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h: In function â€˜downâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h:105: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h: In function â€˜down_interruptibleâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h:130: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h: In function â€˜down_trylockâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h:155: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h: In function â€˜upâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/semaphore.h:179: error: expected â€˜:â€™ or â€˜)â€™ before â€˜KBUILD_BASENAMEâ€™
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/module.h:22,
                 from gunzets.c:28:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/module.h:60:2: error: #error unknown processor family
gunzets.c:31:26: error: linux/malloc.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/irq.h:21,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/asm/hardirq.h:5,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/interrupt.h:10,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/usb.h:15,
                 from gunzets.c:37:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/asm/hardirq.h:5,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/interrupt.h:10,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/usb.h:15,
                 from gunzets.c:37:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/irq.h: At top level:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/irq.h:82: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.17-10-generic/include/linux/irq.h:84: error: â€˜NR_IRQSâ€™ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/irq.h:93,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/asm/hardirq.h:5,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/interrupt.h:10,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/usb.h:15,
                 from gunzets.c:37:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/hw_irq.h:29: error: â€˜NR_IRQ_VECTORSâ€™ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/interrupt.h:10,
                 from /usr/src/linux-headers-2.6.17-10-generic/include/linux/usb.h:15,
                 from gunzets.c:37:
/usr/src/linux-headers-2.6.17-10-generic/include/asm/hardirq.h:12: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.17-10-generic/include/linux/poll.h:11,
                 from gunzets.c:40:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/mm.h: In function â€˜lowmem_page_addressâ€™:
/usr/src/linux-headers-2.6.17-10-generic/include/linux/mm.h:517: warning: implicit declaration of function â€˜page_to_pfnâ€™
/usr/src/linux-headers-2.6.17-10-generic/include/linux/mm.h:517: error: â€˜CONFIG_PAGE_OFFSETâ€™ undeclared (first use in this function)
gunzets.c: At top level:
gunzets.c:48: error: expected â€˜)â€™ before string constant
gunzets.c: In function â€˜gunzets_irqâ€™:
gunzets.c:120: warning: pointer targets in initialization differ in signedness
gunzets.c:124: error: â€˜USB_ST_NOERRORâ€™ undeclared (first use in this function)
gunzets.c:153: warning: pointer targets in passing argument 2 of â€˜gunzets_write_bufferâ€™ differ in signedness
gunzets.c: In function â€˜gunzets_disconnectâ€™:
gunzets.c:175: error: â€˜MOD_DEC_USE_COUNTâ€™ undeclared (first use in this function)
gunzets.c:178:40: error: missing binary operator before token "("
gunzets.c: In function â€˜gunzets_probeâ€™:
gunzets.c:195: error: request for member â€˜altsettingâ€™ in something not a structure or union
gunzets.c:198: error: â€˜struct usb_interface_descriptorâ€™ has no member named â€˜endpointâ€™
gunzets.c:205: warning: implicit declaration of function â€˜usb_set_protocolâ€™
gunzets.c:206: warning: implicit declaration of function â€˜usb_set_idleâ€™
gunzets.c:213: warning: implicit declaration of function â€˜FILL_INT_URBâ€™
gunzets.c:219: error: too few arguments to function â€˜usb_submit_urbâ€™
gunzets.c:238: error: â€˜MOD_INC_USE_COUNTâ€™ undeclared (first use in this function)
gunzets.c: At top level:
gunzets.c:249: warning: initialization from incompatible pointer type
gunzets.c:250: warning: initialization from incompatible pointer type
gunzets.c: In function â€˜gunzets_read_from_bufferâ€™:
gunzets.c:273: warning: ignoring return value of â€˜copy_to_userâ€™, declared with attribute warn_unused_result
gunzets.c: In function â€˜gunzets_openâ€™:
gunzets.c:309: error: â€˜MOD_INC_USE_COUNTâ€™ undeclared (first use in this function)
gunzets.c: In function â€˜gunzets_releaseâ€™:
gunzets.c:325: error: â€˜MOD_DEC_USE_COUNTâ€™ undeclared (first use in this function)
make: *** [gunzets.o] Error 1[/FONT]

I really don’t want to have to post all the other make attempts except to say that I tried:
[FONT="Courier New"]sudo make KERNELDIR=/usr/src/linux-headers-2.6[/FONT]
and
[FONT="Courier New"]sudo make[/FONT]

all of these command were run from the location where I had installed the gunzets files.

So Very sorry for the very long post but can anyone help me? Please?

Thanks

Phill

---

### Post by thomjohns on 2007-03-26
Hi Phil,

I saw your msg here yesterday, and sympathise completely.  I'm a complete noob as well, using Linux to do some things that WinXP can't very well.  I just got a Planar PT1510MX for the touchscreen, and surprise! no good driver for Linux.  Kinda surprising, what with the touchpads going around.

Please excuse me if I get pedantic or say things you may know already.  It's hard to tell what someone's expertise and experience is, so it often helps to get very basic.

Here are some resources that I've found very helpful in trying to keep my head above water.
Linux resources (general):
[http://www.tldp.org/](http://www.tldp.org/),
[http://www.techbooksforfree.com/linux.shtml](http://www.techbooksforfree.com/linux.shtml),
[http://www.linuxtopia.org/online_books/linux_for_beginners_index.html](http://www.linuxtopia.org/online_books/linux_for_beginners_index.html)

Programming and installation:
 [https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/configuring-your-system-chap.html](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/configuring-your-system-chap.html), 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/), 
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide), 
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

and if you have an account through your local library, you might be able to read some Linux books from home.  I've been using Books24x7.com, as they have many good Linux books.

Touchscreen links (some aren't directly applicable, but have useful hints or suggestions):
[http://www.touch-base.com/main.asp?item=2](http://www.touch-base.com/main.asp?item=2), 
[http://www.mp3car.com/vbulletin/linux/55727-touchscreen-changing-usb-event-device-power-off.html](http://www.mp3car.com/vbulletin/linux/55727-touchscreen-changing-usb-event-device-power-off.html), 
[http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html](http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html), 
[http://www.linuxforums.org/forum/mandriva-linux-help/86066-touchscreen-calibration.html](http://www.linuxforums.org/forum/mandriva-linux-help/86066-touchscreen-calibration.html), 
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad), 
[http://aiptektablet.sourceforge.net/xserver.html](http://aiptektablet.sourceforge.net/xserver.html)

Now, for what's relevant to your immediate problem.  Looks like on the face of it there is no cut-and-dried solution.  Again, surprising, considering how proactive Linux programmers are in general.  And documentation is terrible if you're not a developer, so one has to sort through tons 'o stuff and isolate the little gems.  Here's what I found out:

- People in our position should avoid compiling if at all possible, unless everything is handed to us on a plate (make files included, just type ./configure, etc.).  So I did everything in my power to avoid that.  Besides, I really DON'T know what I'm doing, so with my luck I'd break the system.

- Now we're at your question.  They weren't clear in the instructions, but you did it right.  I'll recap.  You have two choices:  use the pre-compiled files or compile yourself.  Unless you like lots of pain and having to decipher cryptic instructions and figure out interrelationships (i.e., futz around for a long time and get an education), use the compiled ones, which are ".o" files (as opposed to ".c" files if you're not a programmer).  Incidentally, I have no idea what the difference is between ".ko" files, ".so" and ".o" files, and I don't care now that it turns out that they do the same thing.

- The xorg.conf file you got right.  I added some additional things, but that's because I used a different driver eventually.

- For figuring out what is going on, system logs are critical, as are system utilities.  So I used utilities like Menu -> System -> KInfoCenter to determine that the system actually did see the Gunze plugged in.  Which meant that it wasn't a USB problem, but what to do with the info once it came over USB (i.e., a driver problem).

  Also I used /var/log/syslog to identify that the different usb ports were being loaded.  Some were EHCI and some were UHCI and I don't care what they were as long as there were no errors.  But that log didn't really tell me anything else.  So went to dmesg and saw the same thing, yippee.  (Oh, and you can "Reload" the file as necessary, no worries).

  Xorg.0.log shows the results from loading the touchscreen drivers, as you see, and I tacked those issues one by one, specifically whether everything was being loaded, where it should go and what kind of errors were resulting.  Since you followed the directions, there is a problem!  Not your fault, but the ground has moved under your feet.  Namely, /dev/gunzets is the wrong thing to put in the xorg.conf.  What no one has told you or me is that /dev/gunzets is some kind of action "flag" or "channel".  Compare to other InputDevices:  Option "Device" is /dev/input/event1 or /dev/input/mouse1.  I made mine /dev/input/event1, so I guess that action triggers the touchscreen (and I also tried mouse1 and ts0, no changes).  Oh, and you can see what actions are currently being linked to devices by entering the command "cat /proc/bus/input/devices", and you should Google that because I'm sure almost anyone can explain it better than I.

  So then I cheated (more).  Or rather, benefited from an earlier desperate ploy on my part - to get a ready-made solution.  I had found (from voluminous searching and references) a site dealing with touchpads.  Touch-base.com, go figure.  They have this wonderful offer to download to one an OS-appropriate touchscreen driver.  But their Linux support is thin.  I seized the opportunity, hoping it would solve all my problems at one stroke.  It didn't.  But, in the course of events when I went back to working on the Gunze driver, it turns out that in installing the Touch-base drivers (and of course I couldn't clean them all out when I tried) a file called "xf86_tbupddlx.o" was installed and my xorg.conf was modded.  When I saw it, it screwed me up when I tried to remove it, so I left it.  Now my Xorg.0.log file was complaining about not finding xf86_tbupddlx, because (of course) the program had automatically installed it in the wrong place.  I figured that two bad drivers in the same right place were better than one (since one wasn't really working), and moved it.  Presto!  Everything now works!

  (I have no idea why, actually.  But I'm not doing anything more to it!)

  But my y direction was reversed and I wasn't interested in compiling, so I needed another configuration program.  Turns out that in the process of installing the Touch-base driver, it also put a couple of config programs on my desktop.  I used those and everything worked out fine.

  BTW, I ended up using the evtouch driver.  It seems to me, after all the pain I went through, that it doesn't really matter which driver you use, as long as the appropriate files are in the right locations.  I have evtouch_drv.so right next to the gunze_drv.o and xf86_tbupddlx.o files.  I did this since the evtouch driver has an option of SwapY, which I thought I needed.  But I'm not sure now, since perhaps the configuration program solved/would have solved it.

To summarize, I moved the gunze_drv.o file to the /usr/lib/xorg/modules/input/ folder, changed the xorg.conf touchsreen "Device" entry to something like /dev/input/event1 (making sure that event existed in that folder), added the driver name to the "Module" section, got and installed the Touch-Base.com driver, moved xf86_tbupddlx.o to the /usr/lib/xorg/modules/input/ folder, and configured the touchscreen.  And rebooted here and there.  I hope I haven't forgotten anything.  I'm sorry if I have.

Here is my resulting xorg.conf file:.

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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
#	ModulePath	"/usr/X11R6/lib/modules"
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
	Load	"evtouch_drv.so"
#	Load	"gunze_drv.o"
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

## TouchKit section begin ( Please do NOT edit this section!! ) ##
#    Section "InputDevice"
#    Identifier "TKPANEL"
#    Driver "touchkit"
#    Option "Device" "/dev/tkdat0"
#    Option "DebugLevel" "0"
#    EndSection
## TouchKit section end ##

Section "InputDevice"
     Identifier                    "touchscreen"
     Driver "evtouch"
     Option "Device"               "/dev/input/event1"
     Option "DeviceName"           "touchscreen"
     Option "MinX"                 "98"
     Option "MinY"                 "43"
     Option "MaxX"                 "940"
     Option "MaxY"                 "925"
     Option "ReportingMode"        "Raw"
     Option "Emulate3Buttons"
     Option "Emulate3Timeout"      "50"
     Option "SendCoreEvents"       "On"
     Option "SwapY"                "1"
 EndSection

Section "InputDevice"
	Identifier                 "Updd0"
	Driver                     "xf86_tbupddlx"
	Option "Device"            "/tbupddlx/comReadPipe"
EndSection

#Section "InputDevice"
#	Identifier "Touchscreen0"
#	Driver "gunze"
#	Option "Device"            "/dev/input/mouse0"
#	Option "Device"            "/dev/input/event1"
#	Option "Device"            "/dev/input/ts0"
#	Option "DeviceType"       "usb"
#	Option "BaudRate"          "9600"
#	Option "Smoothness"        "9"
#	Option "TappingDelay"      "0"
#	Option "JitterDelay"       "50"
#	Option "DebugLevel"        "0"
#	Option "Res12Bit"          "False"
#	Option "SendCoreEvents"
#EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	InputDevice "Updd0" "SendCoreEvents"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
#	InputDevice	"Touchscreen0"
	InputDevice	"touchscreen"
EndSection

Section "DRI"
	Mode	0666
EndSection

--------------------------------------------------------------------------------

Looks like the formatting has gone away, sorry.

I assume that your system will behave the same.  I am definitely no expert.  However, I'm having a beer now because I deserve it after fixing this painful problem.  My conclusion is that documentation in the Linux world, like so many other industries and fields, is not what it should be.  Since I hate documenting too, I can relate, but poor documentation sure doesn't help either in setting up a system or in acceptance of Linux by more people.  Good luck!

Thom

---

### Post by PhillD on 2007-03-27
Hi Thom,

Thanks for your help on this, I had completely given up on using the USB channel and opted for serial instead, the monitor has dual USB/serial capability but the PC I was originally using did not have a serial port.  But after this post I’m going to go back and try USB again.

Thanks again

PhillD

---

### Post by PhillD on 2007-03-28
Hi Thom,

I'm not sure if your still following this post but hopefully you are as I have a few questions.

From the look of your xorg.conf file, the gunze driver is completely commented out and not used at all.  I decided to try the evtouch driver (via serial) just to see what I could do with it but it acts weird.  Every time I touch the screen, the mouse just jumps to a particular point on the screen.  I tried messing with the Min/Max settings etc in the .conf file but this doesn’t seem to help.  I tried to configure it for USB just by using event1 and this didn't work either (not that I expect it to)!

Next I went in pursuit of the touch-base.com driver you mentioned only to find another problem.  The driver is licensed and has to be paid for on each machine where it is used.  I guess this is frowned upon by the Linux community but even more so by my company (they don’t want to pay for something that should work for free).  Besides, I thought Linux and everything associated with it is supposed to be built on open source and freeness.  I didn’t even see the source code listed.

I guess I could also have a newbie rant here about the fact that I have to install java before I could install this driver........Should I? Oh why not??? Why can't things be bloody simple to install on Linux?  For god sake, all I have to do in Windows to install java is double click an exe file, but nooooooooooooooooooooooo, Linux has to be awkward and the instructions are 4 pages long.  Ok, I feel better now.  That wasn;t a rant at you either Thom.

To cut things short, I kinda figure that the driver you installed from touch-base.com is doing all the work for you and the evtouch driver, although setup on event1 isn't actually doing anything at all.  But I am a newbie too and I may be totally wrong but I can't get the evtouch utility to work for me very well at all.  I will continue to mess with the driver and see what I can figure out.  Thanks again for the help

PhillD

---

### Post by PhillD on 2007-03-28
Hi Thom,

Did you have any problems installing the driver from touch-base.com?  How did you install it? did you do the automated install via java? Or did you do the manual install?  If you installed via java, how did you do it?  I supposedly successfully installed java (according to the system messages) but when i type the java command to install the touch base driver, all I get is that the “java” file or folder is not found, like it hasn’t registered the command or something... even if I try it from the Java folder it doesn’t work either.

If you did the manual install did you have any problems?  The instructions told me to copy a file the /etc/rc.d/init.d/ folder but it does not exist.  So I skipped the following commands

cp S90tbupddlx /etc/rc.d/init.d/tbupddlx
-ln -s /etc/rc.d/init.d/tbupddlx /etc/rc.d/rc2.d/S90tbupddlx
-ln -s /etc/rc.d/init.d/tbupddlx /etc/rc.d/rc3.d/S90tbupddlx
-ln -s /etc/rc.d/init.d/tbupddlx /etc/rc.d/rc5.d/S90tbupddlx

I completed everything else in the instructions and it modded my xorg file but when I restarted, the screen remained black.  I had to comment out the new entries in the xorg and was able to restart and get the GUI back.

Any suggestions?

PhillD

---

### Post by thomjohns on 2007-04-01
Hi Phil,
No worries.  It's tough to wade through these things sometimes.  It's entirely possible that that one driver is doing all the work.  I tend to not look at things too closely once they work.  I was messing around with a lot of things at the time, so I'm not sure the exact method, but I do remember that it didn't work right away even after install.  I did install java, basically because I need the functionality for other things.  I suspect that I tried the simple install and the program put everything where **it** thought they should go.

I'd double check that the files are in the correct folders.  Sorry to press the point, but I do remember that I got increased functionality (from nothing to responses to touches to correct y directions to correct touch location) as I got the different files positioned correctly.  Regardless of the method that I used to install, I did use the calibration utility that was installed, and that was the final piece of the puzzle to get it working correctly.

When you look at your xorg.conf file, check the top few lines.  The install process put the 

Section "InputDevice"
Identifier "Updd0"
Driver "xf86_tbupddlx"
Option "Device" "/tbupddlx/comReadPipe"
EndSection

lines at the very top, which was odd.  I didn't like them there (bad organization) so I moved them with the rest.  I commented them out as well and had the same results - had to boot into command line to re-edit them in before it would boot.  That was my first clue they had to remain!

Because of version changes (I suspect), my init.d folder is in /etc/.  There's no rc.d folder anymore I guess.  That means that where the programs are looking is changing.  In response to the inevitable question, I have no S90tbupddlx or tbupddlx file in that folder and there are no daughter folders.

Alright, now that you're asking "how", I'm taking a closer look at things.  I'll agree with you that that driver is probably doing everything.  Looking at the xorg.conf entries, rather than going with a /dev/event entry, it looks like it refers to a directory at the root level "tbuppdlx".  Sure enough, one has been made for me!  Wow, it's so nice to see that this company is playing by the rules of Linux directory formulation.  Actually, reminds me of the Windows practice of companies just throwing in their program at the c: drive level to make it easy on themselves, rather than being courteous and neat and placing their programs in "Program Files" like normal people.  Sigh.  A Windows rant, I guess.

That folder created at the root includes .so files, making me think it's the driver location.  Looks like everything's in there.  I'd copy everything over by hand, but you won't get the benefit of the calibration utility without java.  I'm looking to see if there are calibration constants in any of the readable files...

I suspect that inside of tbcalib.xpm is where the calibration constants may be stored.  But I'm not sure how to confirm that or to figure which ones are the right ones to use to change calibration.  Sorry.

I think that I'm also going to have to go back to the drawing board to use another driver, since this company seems to not be open-source.  TANSTAAFL.  Oh well.  There is a certain trial period I believe, and hopefully I can figure the screen out before it expires.  Hope this has helped, Phil.

Oh, BTW, I tried serial briefly, but the computer I was using didn't care for it at all.  However, I didn't try it further so I would assume that it's possible to make it work.  The data rate isn't very high, so that method should work fine.

Thom

---

### Post by PhillD on 2007-04-02
Hi Thom,

Thanks again for your help on this.

I have actually had some success in using the gunze driver with serial configuration.  The only obstacle now is to overcome the calibration process which crashes during use (It took me a while to get to that point too!).

I would love to use USB because it is my preferred connection, but I guess using USB in Linux can be quite complicated (compared to serial).  I wish I understood the USB problem more/ how it works / maps the physical ports to the data channels in the system, but I just don’t have time to research it as I've still got a lot of other things to setup on this box (printer/wireless etc..)

If this was a personal project, I'd take my time and probably end up a linux programmer before I came back to this.....but this is for a business and I've been instructed to "get a linux box out there" as soon as possible.

Regarding the usb driver, if I was able to get it to work, I would need to buy it for 25 + PC's...With my companies track record of licensing, that would be a hard thing to accomplish with a small driver/easy oversight such as this.......but then again, that’s what I get for trying to do things properly.  (hey' that would make a great signature).

Phill

---


---
title: "Synaptics with adb touchpads"
date: 2007-03-10
forum: Apple PPC Users
---

### Post by NiN on 2007-03-10
Hi!

I've just found a patch that lets you use your adb touchpad (found on some older models of power and ibooks) with the synaptics driver.

It can be found here: [http://www.cs.unibo.it/~bigoi/](http://www.cs.unibo.it/~bigoi/) - Thank you!

I've filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/91112](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/91112)

Hopefully this will be soon included :)


HOWTO:

Open a terminal.

First check, if you have such a touchpad:
```

cat /proc/bus/input/devices

```

If the output contains the following:
```

I: Bus=0017 Vendor=0001 Product=3301 Version=0100
N: Name="ADB mouse"
P: Phys=adb3:3.01/input

```

Then continue, else this won't help you!

You have to get the patch from [http://www.cs.unibo.it/~bigoi/kernel_patch/cur/adbsyn_0.3-2.6.19.diff](http://www.cs.unibo.it/~bigoi/kernel_patch/cur/adbsyn_0.3-2.6.19.diff)

Then install the following:
```

apt-get install kernel-package build-essential linux source fakeroot

```

Untar your kernel sources somewhere:
```

cd <temporary working path>
tar -xvjpf /usr/src/linux-source-2.6.20.tar.bz2

```

Then patch the sources
```

cd <path to sources>/drivers/macintosh
patch -p1 -i <path to patch>/adbsyn_0.3_2.6.19.diff

```

This will not work automatically, just type in the file name that is conflicting.

Now copy the kernel configuration you are using and activate the patch:
```

cd <temporary working path>/linux-source-2.6.20
cp /boot/config-`uname -r` .config
make menuconfig

```

Now activate the support:
```

Device Drivers --> Macintosh device drivers --> Enable absolute mode for adb trackpads

```

Now compile your new kernel with
```

make-kpkg --initrd --bzimage --rootcmd fakeroot buildpackage

```

This will take a while.

When finished You should have dome .deb files.
install them using
```

sudo dpkg -i ../*.deb

```

That's it. Now you can use your trackpad with synaptics.

---

### Post by kapatp on 2007-04-04
I was trying this with the new feisty beta release for Kubuntu. The kernel compilation process seemingly went well with warnings here and there..

Then when I tried to install the deb packages I got the following error:
```

Setting up linux-image-2.6.20.3-ubuntu1 (2.6.20-14.22) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.20.3-ubuntu1)
dpkg: error processing linux-image-2.6.20.3-ubuntu1 (--install):
 subprocess post-installation script returned error exit status 2
Setting up linux-manual-2.6.20.3-ubuntu1 (2.6.20-14.22) ...
Setting up linux-source-2.6.20.3-ubuntu1 (2.6.20-14.22) ...

Errors were encountered while processing:
 linux-image-2.6.20.3-ubuntu1

```

What should I do??
Thanks
pk

---

### Post by kapatp on 2007-04-06
OK, I am getting back with the solution, and possibly a bug. Hopefully this might help someone else:
The final step
```
sudo dpkg -i ../*.deb
```
was giving the following error:
```

Setting up linux-image-2.6.20.3-ubuntu1 (2.6.20-14.22) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.20.3-ubuntu1)
```

I don't know why it is looking for */boot/vmlinu**z**-2.6.20.3-ubuntu1*!!! That is absent but */boot/vmlinu**x**-2.6.20.3-ubuntu1* is present (z vs x), so I created a symlink manually:
```

cd /boot
sudo ln -s vmlinux-2.6.20.3-ubuntu1 vmlinuz-2.6.20.3-ubuntu1
```

Also there was some errors of not being able to find */lib/firmware/2.6.20.3-ubuntu1*, which is expected I guess. So, the same trick:
```

cd /lib/firmware
sudo ln -s 2.6.20-13-powerpc 2.60.20.3-ubuntu1
```
Note here that *2.6.20-13-powerpc* folder already existed. Then a 
```
sudo dpkg --configure -a
```
solved everything nicely.

But  because of all these wrong filenames, the correspondence between *vmlinux* and *initrd.img* files in /boot were screwed. So I had to edit */etc/yaboot.conf* and change the "image" sections accordingly, making sure that the correct intird.img file is used with the corresponding vmlinux file. Instead of using the symlinks of */boot/vmlinuz* or */boot/vmlinux.old*, I prefered using the direct filenames: */boot/vmlinux-2.6.20.3-ubuntu1* and */boot/initrd.img.2.6.20.3-ubuntu1*. [B]And yes, remember to run
```
sudo /usr/sbin/ybin
```
after editing the yaboot.conf[/B]. I didn't and messed up; had to use a rescue disk to boot up, mount the partitions; run ybin with proper parameters; restart into default kernel; run ybin again to enable the bootstrap partition properly; only then things were on track.

BUT after all these efforts, the trackpad didn't seem to work! I used *ksynaptics* to increase the sensitivity of the touchpad to "high". Ok now, the touchpad is working but is extremely clumsy. Still trying to figure out if this can be smoothed out. Otherwise the whole exercise of kernel compilation would be futile. Oh yes, if the iBook is an old model (which mine is: 2004 spring) **only a single tap works (as used to in OSX). None of the fancy scrolling or multi finger taps are recognized: of course that is a hardware limitation**, I guess.

pk

---

### Post by guidop on 2007-12-31
I've finally gotten this to work reasonably well on my 1.0GHz 12-inch Powerbook.
Two finger and three finger touch detection does not seem to work, but I am able to set the upper left and upper right corners to emulate mouse buttons 2 and 3.

The homepage for the ADB trackpad kernel patch is now at this address:

[http://adbsyn.crisidev.org/]("http://adbsyn.crisidev.org/")


Once the patched kernel is installed, I suggest editing /etc/X11/xorg.conf to contain at least the following parameters in the touchpad section, and restarting X:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option          "SHMConfig"             "on"
.
.
.
EndSection

```
To determine the x and y limits of the trackpad, run synclient in a terminal window, and trace the area with one finger.  This will also verify that the kernel patch works and absolute x and y information is being sent from the trackpad.
```

$ synclient -m 100

```
One can also use synclient to determine the current settings of the trackpad.
```

$ synclient -l  # Lowercase Letter L

```
I found that the x range of my trackpad is about 318-1448, and the y range about 200-1000.  Synclient can the be used to set the left, right, top and bottom limits for scrolling and button emulation.  I have fairly fat fingers, so I made the edge regions fairly wide.
```

$ synclient LeftEdge=440
$ synclient RightEdge=1380
$ synclient TopEdge=440
$ synclient BottomEdge=900

```
It may also be a good idea to set the tap sensitivity and button 2 and 3 emulation at this point.  Best settings will vary based on the z values synclient shows when touching the trackpad, and one's preference.  

In my case, I also found that a key to getting a reliable button press required setting the MaxTapMove parameter much larger value than the default value of 4.
```

$ synclient FingerLow=3
$ synclient FingerHigh=10
$ synclient RTCornerButton=3
$ synclient LTCornerButton=2
$ synclient MaxTapMove=250

```
I also disabled trackpad tapping, and put mouse button 1 in the lower left, nothing in the lower right
```

$ synclient TapButton1=0
$ synclient TapButton2=0
$ synclient TapButton3=0
$ synclient LBCornerButton=1
$ synclient RBCornerButton=0

```

At this point, I suggest opening a separate terminal window and running xev to verify that you can reliably get emulated button presses and scroll events (reported as button 4 and 5 events for vertical scroll, 6 and 7 for horizontal).  The vertical scroll region should be on the right side, and horizontal on the bottom.
```

$ xev

```
I used synclient to modify parameters and xev to check results until I was happy with my settings, then modified xorg.conf to make them permanent.
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option          "SHMConfig"             "on"

        Option          "LeftEdge"              "440"
        Option          "RightEdge"             "1380"
        Option          "TopEdge"               "440"
        Option          "BottomEdge"            "900"
        Option          "FingerLow"             "3"
        Option          "FingerHigh"            "10"
        Option          "MaxTapMove"            "250"
	Option		"RTCornerButton"	"3"
	Option		"RBCornerButton"	"0"
	Option		"LTCornerButton"	"2"
	Option		"LBCornerButton"	"1"
	Option		"TapButton1"		"0"
	Option		"TapButton2"		"0"
	Option		"TapButton3"		"0"
EndSection

```

Here is my current synclient parameter listing.  Some values are defaults, and don't need to be set in xorg.conf.  Your settings and defaults may vary.
```

$ synclient -l
Parameter settings:
    LeftEdge             = 440
    RightEdge            = 1380
    TopEdge              = 440
    BottomEdge           = 900
    FingerLow            = 3
    FingerHigh           = 10
    MaxTapTime           = 400
    MaxTapMove           = 250
    MaxDoubleTapTime     = 200
    SingleTapTimeout     = 250
    ClickTime            = 70
    FastTaps             = 0
    EmulateMidButtonTime = 75
    VertScrollDelta      = 50
    HorizScrollDelta     = 0
    VertEdgeScroll       = 1
    HorizEdgeScroll      = 0
    VertTwoFingerScroll  = 0
    HorizTwoFingerScroll = 0
    MinSpeed             = 0.25
    MaxSpeed             = 0.75
    AccelFactor          = 0.06
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 80
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    LeftRightScrolling   = 0
    UpDownRepeat         = 1
    LeftRightRepeat      = 1
    ScrollButtonRepeat   = 100
    TouchpadOff          = 0
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 3
    RBCornerButton       = 0
    LTCornerButton       = 2
    LBCornerButton       = 1
    TapButton1           = 0
    TapButton2           = 0
    TapButton3           = 0
    CircularScrolling    = 0
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 0
    CircularPad          = 0
    PalmDetect           = 0
    PalmMinWidth         = 10
    PalmMinZ             = 200
    CoastingSpeed        = 20
    PressureMotionMinZ   = 30
    PressureMotionMaxZ   = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1

```

I also found the synclient and synaptics man pages helpful in at least giving a brief description of the synaptics parameters:
```

$ man synclient
$ man synaptics

```
The qsynaptics GUI may make tuning a bit easier, but I did not try it.

Hope this helps someone else get their ADB trackpad tuned to their liking.

---

### Post by robiouilliame on 2008-07-07
Hi !

I need some help. I'd kill to have scrolling on my ibookG4 touchpad under linux, that's why i keep using ageing macos 10.3. So i've tried the explainations above, i've patched a 2.6.24-19 kernel and compiled it (Ubuntu 08.04), and my "buggy" touchpad became useless. I tried with a 2.6.23 kernel, but i got the same result. I must have done something wrong, but i can't figure out what. So i keep using my unpatched 2.6.24-19 kernel with it's scrollingless and buggy touchpad.
I can send my .config if it can help. 
If you can help another desperate iBookG4 under linux user, i'd be the happiest.

---

### Post by robiouilliame on 2008-07-08
Ooops ! Sorry I bothered you folks ! I was "sure" I had got rid of mouseemu before I came here crying... 
So, all I had to do was to uninstall mouseemu and all the touchpad applets included in Ubuntu.
No use to say I'm happy tonight !

---

### Post by evaroberts on 2008-07-09
Interesting is the fact, Isn't it?? Synaptics with adb touchpads.
Well i have recently got a new ibookG4 touchpad. But there are certain problems i faced when shifting from Windows to linux.
It has become so slow can anyone help me with it?
=================
eva
[Used Apple Laptops](http://applelaptopshop.com)

---


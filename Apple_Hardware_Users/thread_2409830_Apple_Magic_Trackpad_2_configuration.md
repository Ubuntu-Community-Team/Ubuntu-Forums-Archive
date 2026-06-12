---
title: "Apple Magic Trackpad 2 configuration"
date: 2019-01-07
forum: Apple Hardware Users
---

### Post by 360-dennis on 2019-01-07
I set out to get the Apple Magic Trackpad 2 (i've shortened it to AMT2) to work, this post is ment to share my experiences, to dump 50 tabs of my browser in this post and to ask some questions. I'm not a expert on ubuntu desktops, although i'm an enthousiast. Hopefully this thread will get all the how to get AMT2 working. If it's usefull, I will make some efforts to incorporate it into the official Ubuntu documentation although It will be my first doing so. 

> What is the magic trackpad 2? 
Basicly an external trackpad ment for apple laptops:
[https://en.wikipedia.org/wiki/Magic_Trackpad_2](https://en.wikipedia.org/wiki/Magic_Trackpad_2)

> How do I install the hardware driver for the AMT2?
You don't, most of the linux hardware drivers reside in the kernel. The AMT2 drivers are in the 4.20 kernel, which isn't incorparated (yet) in an official ubuntu flavor. Yu can find the used kernel vs ubuntu version here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
To install newer kernels, I recommend using ukuu:
[https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)

> How to check if your AMT2 is recognised?
open a terminal and run:
xinput list
It should list a "Apple Inc. Magic Trackpad 2" device. Write down the id number, you will need this later. 

> Does your AMT2 only work if you press it really hard (almost to a click or even after a click)? You will probably have to change the pressure sensitivity:
This is due to defaults which aren't right (just yet). I expect to be corrected after the linux kernel 4.20 is incorporated into the kernel. If we find the correct settings in this post, I will try to find out how we will get the correct defaults in ubuntu. 
First find out if you are using libinput or synaptics as main driver in your system:
xinput list-props [DEVICE ID]
replace the [DEVICE ID] with the id you wrote down earlier. You should get the properties of the AMT2, which should say "Device 'Apple Inc. Magic Trackpad 2'".
Set the finger options:
xinput set-prop [DEVICE ID] [FINGER PROPERTY ID] 2, 2, 0
So in my case this looks like
xinput set-prop 17 296 2, 2, 0

More information here:
- explaination of xinput: 
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
- settings of synaptics and the finger options: 
[http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html)
same as [https://www.x.org/releases/X11R7.6/doc/man/man4/synaptics.4.xhtml](https://www.x.org/releases/X11R7.6/doc/man/man4/synaptics.4.xhtml)

> Do you want to use the 3 finger click as the middle mouse button (paste the selection).
open a terminal and configure:
synclient TapButton3=2
More details here:
[https://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click](https://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click)

> Make the changes stick (so you won't have to set the settings every time you connect the AMT2). 
Not sure yet what the best approach is, I'm using the shell startup script for now like described here:
[https://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click](https://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click)
But this might work:
[https://www.dell.com/support/article/nl/nl/nlbsdt1/sln308258/precision-xps-ubuntu-general-touchpad-mouse-issue-fix?lang=en](https://www.dell.com/support/article/nl/nl/nlbsdt1/sln308258/precision-xps-ubuntu-general-touchpad-mouse-issue-fix?lang=en)


Todo/questions:
- I haven't tried the bluetooth config yet, I think I have some issues with my bluetooth broadcom hardware in my Dell XPS13-9350. I'm about to swap the broadcom chip with the intel, after that I will give the bluetooth driver a go. From what I've read the experience should be the same as with the wired config. 
- I haven't yet tried to configure gestures, what should be the way to go? I was thinking of describing a few options like
[https://www.omgubuntu.co.uk/2018/09/linux-touchpad-gestures-app](https://www.omgubuntu.co.uk/2018/09/linux-touchpad-gestures-app)
[https://askubuntu.com/questions/1034624/touchpad-gestures-in-ubuntu-18-04-lts](https://askubuntu.com/questions/1034624/touchpad-gestures-in-ubuntu-18-04-lts)
Are these the best options? And what is preferred? I would like it to contain  the easiest, but also include expert options. 
- I'm using kubuntu 18.04 now, but I did use xubuntu, ubuntu-gnome, ubuntu-unity. It seems every desktop manager has their own preference on how to configure the touchpad. Is that correct? Should this guide contain guidance on the main ubuntu desktop managers to get the AMT2 working? I think I would stick to the latest LTS versions.
- Should AMT2 use libinput or synaptics? Did I understand correcty that Wayland prefers libinput so for future Ubuntu versions libinput is preferred? If so, I think this guide should contain configuring AMT2 with libinput, am I correct? 
- How do I configure the AMT2 to prefer libinput instead of synaptics? I only found posts of switching to libinput for all devices, but I want it to be for the AMT2 only. Should it be through  /usr/share/X11/xorg.conf.d/50-synaptics.conf or is that outdated in 18.04? I found another recent post here:
[https://askubuntu.com/questions/1031940/how-to-switch-from-libinput-to-synaptics-in-ubuntu-18-04](https://askubuntu.com/questions/1031940/how-to-switch-from-libinput-to-synaptics-in-ubuntu-18-04)
- And If it uses libinput, should I configure the touch sensitivity like this: [https://www.reddit.com/r/linuxquestions/comments/ad0bez/needing_a_bit_of_help_regarding_libinput_on_ubuntu/](https://www.reddit.com/r/linuxquestions/comments/ad0bez/needing_a_bit_of_help_regarding_libinput_on_ubuntu/)
[https://askubuntu.com/questions/1099785/how-do-i-increase-touch-pad-senstivity-using-libinput](https://askubuntu.com/questions/1099785/how-do-i-increase-touch-pad-senstivity-using-libinput)
- "libinput debug-gui" or "libinput quirks" or "libinput list quirks" does not work in my xubuntu 18.04. Is this correct? It's the same like this post:
[https://stackoverflow.com/questions/50274218/getting-raw-multitouch-data-with-libinput](https://stackoverflow.com/questions/50274218/getting-raw-multitouch-data-with-libinput)
I can't find a mention of this here:
[https://wayland.freedesktop.org/libinput/doc/latest/device-quirks.html](https://wayland.freedesktop.org/libinput/doc/latest/device-quirks.html)

So.. this took my whole morning, I'm looking forward to your comments!

---

### Post by 360-dennis on 2019-01-18
i didn't get much replies here, so i posted it on reddit instead:
[https://www.reddit.com/r/Ubuntu/comments/ahgbdg/apple_magic_trackpad_2_configuration_on_kubuntu/](https://www.reddit.com/r/Ubuntu/comments/ahgbdg/apple_magic_trackpad_2_configuration_on_kubuntu/)

---

### Post by kevin160 on 2019-01-21
Yes, it is absolutely INSANE that trackpad functionality is so incredibly tied to what desktop you are using.  Even the various Ubuntu flavors are all over the place.  It's the same with touch screens.  Why hasn't Linux taken off on the desktop?  This.  

I don't know if you've seen these blog posts but they are quite recent and in depth.  I found them very helpful tuning my macbook's trackpad:

[https://williambharding.com/blog/technology/toward-a-linux-touchpad-as-smooth-as-macbook-pro/](https://williambharding.com/blog/technology/toward-a-linux-touchpad-as-smooth-as-macbook-pro/)
[https://williambharding.com/blog/linux-to-macbook/linux-with-a-macbook-touchpad-feel-pt-2/](https://williambharding.com/blog/linux-to-macbook/linux-with-a-macbook-touchpad-feel-pt-2/)
[https://williambharding.com/blog/technology/linux-touchpad-like-a-macbook-goal-worth-pursuing/](https://williambharding.com/blog/technology/linux-touchpad-like-a-macbook-goal-worth-pursuing/)

And, of course, Arch Linux's always superb documentation that is useful for ubuntu in spite of varying config file locations:

[https://wiki.archlinux.org/index.php/Libinput](https://wiki.archlinux.org/index.php/Libinput)
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)

I would suggest outlining libinput since it is the "future" and also talking about synaptics as a fallback for the extra tunables.  I'm still using synaptics on my macbook because everything else has terrible palm detection.  

Writing executable startup shell scripts is very much frowned upon because of potential blocks and race conditions.  Use the config files if you can.  The numerical order of the files in /usr/share/X11/xorg.conf.d/ is *supposed* to determine what is loaded first.  Unfortunately, it doesn't appear to be quite that simple, since I had to leave libinput first for the synaptics driver to load at all, and then comment extra settings out of the synaptics file.  You'll have to experiment, I think.  I believe you are actually supposed to put your local modifications in /etc/X11/xorg.conf.d/ (yes, create the directory) so your custom files don't get overwritten by upgrades.  

Yes, it does look like libinput quirks isn't in Ubuntu 18.04's libinput-utils.  A newer version is probably needed.  It looks like Disco will have it.  

I have no opinion on gestures, other than to say try to match the mac's defaults for people dual-booting.

---

### Post by leandro-maniezo on 2019-04-03
I'm using ubuntu 18.04 on a Sony Vaio VPC, the Magic Trackpad 2 works just with one finger, I'd like to set it to work at least two finger scrolling.


Have you tried xinput, libinput and interfaces, but without success, have any tips to help?


Thank

---

### Post by crackers_altitude on 2020-01-17
There hasn't been an update to this thread in a while - I'm looking for a touchpad / trackpad for my desktop (not laptop) running :

18.04.3 LTS
Linux kernel 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

What can I look for to know how much functionality, if any, the Apple Magic Trackpad 2 will provide - in USB or Bluetooth configurations? It looks to be challenging if the device works only sort-of. Is there a Bluetooth card or USB dongle that works best?

I've also looked at [https://github.com/robotrovsky/Linux-Magic-Trackpad-2-Driver](https://github.com/robotrovsky/Linux-Magic-Trackpad-2-Driver) which suggests this should be straightforward...

thanks

---

### Post by 360-dennis on 2020-01-22
Look at these threads:
[https://www.reddit.com/r/Ubuntu/comments/ahgbdg/apple_magic_trackpad_2_configuration_on_kubuntu/](https://www.reddit.com/r/Ubuntu/comments/ahgbdg/apple_magic_trackpad_2_configuration_on_kubuntu/)
[https://www.reddit.com/r/Ubuntu/comments/clrj69/magic_trackpad_2_and_1904/fc8hhcy/?context=3](https://www.reddit.com/r/Ubuntu/comments/clrj69/magic_trackpad_2_and_1904/fc8hhcy/?context=3)

Don;t use the robotrovsky project, that project was ment before the drivers were implemented in the kernel.

---

### Post by crackers_altitude on 2020-01-23
Well, I just plugged one in, and I'm delighted to learn it moves the pointer and does single click right out of the box, no fuss.

I have to figure out if I can do anything else with it. I'll report back if I learn any helpful tips to other users who might find this thread.

---

### Post by crackers_altitude on 2020-01-24
I'm going to post to this thread as I get the AMT2 working on my system - as a DIY / how-to. if that's ok. because this is confusing to me. My system is also somewhat precarious, having an undiagnosed - but persistent -problem with the Desktop or login.

SUMMARY SO FAR : it seems the old mouse has a bunch of configurations left in the system, but despite being disconnected, the AMT2 can still function. And though libinput appears to be working, there are other ... wrappers?... specifically, libinput-gestures, which advertises the type of multi-finger input gestures a touchpad allows. But it seems I either have to remove the old optical mouse, or... Not sure.

A couple things I do not understand : 

* while I can view a whole list of functions of the AMT2 using xinput list-props 9, it is not clear how to change these settings to obtain expected results. The descriptions e.g. "libinput Scroll Methods Available (282): 0, 0, 1" do not sound encouraging for getting two-finger swipe scroll working. I

* by now, I'd have expected a number of touchpads to have standard functionality in Ubuntu - e.g. can use apt to install packages at most. Perhaps this functionality is sitting right on the system and I do not understand what it is?

What follows is notes on the adventuring to get advanced functionality to the AMT2 on an Ubuntu 18.04.3 system:

[ looks at links and beyond ]
  
note that Settings has "Mouse & Touchpad", with the following options :
General : Primary Button [ left ][ right ]
Mouse : Mouse speed ; Natural scrolling
Test Options : single-click OK ; double-click OK ; translation OK. Scrolling : not working
"Wacom Tablet" section : no tablet detected.

current system :
libinput : no. this is for configuration with GNOME 
synclient : no. synclient is a CL util to query/modify Synaptics driver options.
Synaptics TouchPad : hardware product from a company named Synaptics.

Xorg.0.log says X Server 1.19.6 Release Date: 2017-12-20, X Protocol Version 11, Revision 0

->** This was not the most recent Xorg.*.log - Xorg.2.log was **
furthermore, I cannot locate the Xorg.*.log for the most recent X session.
UPDATE: I discovered that Xorg.0.log is being written to ~/.local/share/xorg/Xorg.0.log, and furthermore, that EE is found in it - specifically, cannot open /dev/fb0.

Build OS : Linux kernel 4.4.0-148-generic x86_64
Current OS : 4.15.0-74-generic #84-Ubuntu SMP
Ubuntu 18.04.3 LTS bionic

libinput :

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Apple Inc. Magic Trackpad 2                 id=9    [slave  pointer  (2)]

[ try program that monitors touchpad events in real time - makes lots of output ] 

OK, so far so good.

/usr/share/X11/xorg.conf.d :
a number of .conf files, e.g: 40-libinput.conf : contains lines : 

Section "InputClass"
        Identifier "libinput touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
EndSection

... I think this is where there should be a file such as 70-synaptics.conf, as described on the Arch Linux site for the Synaptics TouchPad.

... at this point, need to regroup : it'd be nice to at least get a sort of scroll/flick effect - e.g. two fingers flick up or down to scroll, akin to middle-mouse-wheel. 

must pick this up later...

searching suggests to focus on trying ~/.conf/libinput-gestures.conf - which I guess is part of the libinput which I need to install...

ah - let me try : 

gsettings list-recursively | grep pad
org.gnome.desktop.peripherals.touchpad send-events 'enabled'
org.gnome.desktop.peripherals.touchpad natural-scroll true
org.gnome.desktop.peripherals.touchpad tap-to-click false
org.gnome.desktop.peripherals.touchpad two-finger-scrolling-enabled true
org.gnome.desktop.peripherals.touchpad left-handed 'mouse'
org.gnome.desktop.peripherals.touchpad click-method 'fingers'
org.gnome.desktop.peripherals.touchpad speed 0.0
org.gnome.desktop.peripherals.touchpad scroll-method 'two-finger-scrolling'
org.gnome.desktop.peripherals.touchpad tap-and-drag true
org.gnome.desktop.peripherals.touchpad edge-scrolling-enabled false
org.gnome.desktop.peripherals.touchpad disable-while-typing true

xinput list-props "Apple Inc. Magic Trackpad 2"
Device 'Apple Inc. Magic Trackpad 2':
    Device Enabled (145):    1
    Coordinate Transformation Matrix (147):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Natural Scrolling Enabled (280):    1
    libinput Natural Scrolling Enabled Default (281):    0
    libinput Scroll Methods Available (282):    0, 0, 1
    libinput Scroll Method Enabled (283):    0, 0, 1
    libinput Scroll Method Enabled Default (284):    0, 0, 1
    libinput Button Scrolling Button (285):    2
    libinput Button Scrolling Button Default (286):    2
    libinput Middle Emulation Enabled (287):    0
    libinput Middle Emulation Enabled Default (288):    0
    libinput Accel Speed (289):    0.183824
    libinput Accel Speed Default (290):    0.000000
    libinput Accel Profiles Available (291):    1, 1
    libinput Accel Profile Enabled (292):    1, 0
    libinput Accel Profile Enabled Default (293):    1, 0
    libinput Left Handed Enabled (294):    0
    libinput Left Handed Enabled Default (295):    0
    libinput Send Events Modes Available (265):    1, 0
    libinput Send Events Mode Enabled (266):    0, 0
    libinput Send Events Mode Enabled Default (267):    0, 0
    Device Node (268):    "/dev/input/event4"
    Device Product ID (269):    1452, 613
    libinput Drag Lock Buttons (296):    <no items>
    libinput Horizontal Scroll Enabled (297):    1

... ok, here we go : sudo apt install libinput

Device:           Apple Inc. Magic Trackpad 2
Kernel:           /dev/input/event4
Group:            4
Seat:             seat0, default
Capabilities:     pointer 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *button
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   flat *adaptive
Rotation:         n/a

...[ restart system, restart X ]

notice that my old Logitech USB Optical Mouse is in Xorg.0.log : 

[  1955.529] (II) event4  - Logitech USB Optical Mouse: is tagged by udev as: Mouse
[  1955.529] (II) event4  - Logitech USB Optical Mouse: device is a pointer


... event4 can be used with evtest to read the AMT2 signals. no other relevant keywords (Apple, touch, track, pad, ...) show up in Xorg.0.log. also find libinput : 

[   497.956] (**) Logitech USB Optical Mouse: Applying InputClass "libinput pointer catchall"
[   497.956] (II) Using input driver 'libinput' for 'Logitech USB Optical Mouse'


[ take a break]
... ok, looks like there's something called libinput-gestures and libinput-tools. tools is available from apt (without fuss), but not libinput-gestures. so - not sure about that.

looks like there are two general approaches to gestures, and the window manager (GNOME or other), matters - maybe : 

fusama
libinput-gestures

these packages are not standard as of Ubuntu 18.04.03. I might just have to try one. One important factor is adding the user to the input group using gpasswd.

[ ... coffee ...]

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch) <- overview of multitouch (what I think I actually want) in Ubuntu
[https://wiki.ubuntu.com/Multitouch/Definitions](https://wiki.ubuntu.com/Multitouch/Definitions) <- getting the language correct
[https://wiki.ubuntu.com/Multitouch/HardwareSupport](https://wiki.ubuntu.com/Multitouch/HardwareSupport) <- "Apple Magic Trackpad" is listed here with 10 supported touches since Ubuntu 10.10
[https://wiki.ubuntu.com/Multitouch/TouchpadSupport](https://wiki.ubuntu.com/Multitouch/TouchpadSupport) <- helpful reading - xinput, X, Ubuntu, how it all hangs together...

because that page refers to it, I think it is time to install xserver-xorg-input-synaptics

... `synaptics` returns "Couldn't find synaptics properties. No synaptics driver loaded?"...(I did a Ctrl-C by mistake while it was installing...) now I see /usr/share/X11/xorg.conf.d/70-synaptics.conf, and 51-synaptics-quirks.conf ...

.. copy the example file found here:

[https://gist.github.com/roghnin/eeb6ec519271ec8235a6b42a4820a9b5](https://gist.github.com/roghnin/eeb6ec519271ec8235a6b42a4820a9b5)

... to /usr/share/X11/xorg.conf.d/70-synaptics.conf

.... reboot, see what happens...

nope. dmesg shows interesting info..

sudo apt install touchegg

... nope....
... ugh...
look in 70-synaptics.conf :

# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# [http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html](http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html)
       MatchDevicePath "/dev/input/event*"
^^^^ comment this line IN. try it out...

---

### Post by crackers_altitude on 2020-02-06
interesting information : Google contributed patches to the Linux kernel in December of 2018 :

[https://git.kernel.org/pub/scm/linux/kernel/git/jikos/hid.git/commit/?h=for-next&id=9d7b18668956c411a422d04c712994c5fdb23a4b](https://git.kernel.org/pub/scm/linux/kernel/git/jikos/hid.git/commit/?h=for-next&id=9d7b18668956c411a422d04c712994c5fdb23a4b)

that's for kernel 4.20 - ubuntu appears to be at 4.15.0-76-generic.

---

### Post by energeticsky on 2020-02-24
Hey did you ever figure this out? i have the same problem still trying to get 2 finger scrolling but apple track pad 2 reads "libinput Scroll Methods Available (267):	0, 0, 1"

---

### Post by crackers_altitude on 2020-02-27
> **energeticsky said:**
> Hey did you ever figure this out? i have the same problem still trying to get 2 finger scrolling but apple track pad 2 reads "libinput Scroll Methods Available (267):    0, 0, 1"

no. 

I have asked other questions attempting to figure this out- e.g:

[https://ubuntuforums.org/showthread.php?t=2435862](https://ubuntuforums.org/showthread.php?t=2435862)

I am hoping that the AMT2 will "just work" if kernel 4.20 ends up in Ubuntu 18.04 - because the patches that Google released were for kernel 4.20. otherwise, I am hoping something else turns up.

how did you find libinput scroll methods available?

---

### Post by 360-dennis on 2020-04-16
There is not much confi needed anymore (at least in my case), look at:
[https://www.reddit.com/r/Ubuntu/comments/clrj69/magic_trackpad_2_and_1904/](https://www.reddit.com/r/Ubuntu/comments/clrj69/magic_trackpad_2_and_1904/)

---

### Post by crackers_altitude on 2020-10-02
I just upgraded to 20.04.1 LTS focal, linux 5.4.0-48-generic and Apple magic trackpad 2 works with two-finger scroll and tap to click (I can't be bothered to look up the precise definitions of these things).

nice!

---


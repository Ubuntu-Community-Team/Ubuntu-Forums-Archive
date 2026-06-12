---
title: "installing python-dev"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by dchen37 on 2007-06-16
Hello,

I'm trying to build SynCE but keep getting an error saying python bindings aren't installed.  When I try to apt-get or use synaptic to install python-dev or python2.5-dev I get the following error:


The following packages have unmet dependencies:
  python-dev: Depends: python (= 2.5.1~rc1-0ubuntu3) but 2.5.1-0ubuntu3 is to be installed
              Depends: python2.5-dev (>= 2.5.1~rc1) but it is not going to be installed
E: Broken packages


Anyone know what's up with this?

Also, I can't get my touchpad to work on my Medion notebook if anyone else had had issues with that.

Thanks!

---

### Post by 5-HT on 2007-06-16
For the python problem: looks lke a version mismatch betweeen python and python-dev as python is a dependency for python-dev.Are you running Feisty? Which version of python do you have installed (2.5.1-0ubuntu3?) and where did you install it from? Looking at the repos, Feisty's python and python-dev should both be 2.5.1~rc1-0ubuntu3.
I'd double check your /etc/apt/sources.list to make sure everything's in order and force the install of both python and python-dev (both 2.5.1-0ubuntu3) to get it to work, but it should do that by default anyways. Alternatively, you could grab both python and python-dev from packages.ubuntu.com and install the debs manually..

For the touchpad, do you know who makes it (Synaptics, Alps, etc...)? That would dictate the driver you need to use, and how you should set it up in your x config.

cheers,

---

### Post by dchen37 on 2007-06-16
Thanks for your help.  I'm running feisty.  Not sure where I downloaded python from or if I downloaded a different version that came with the install CD.  How can I check to see if my sources file is up to date?  I tried installing python2.5_2.5.1~rc1-0ubuntu3_i386.deb from packages.ubuntu.com but it gives me "Error: a later version is already installed" although in Synaptic it says I have version 2.5.1-0ubuntu1.

As for the touchpad, I think it's made by synaptic but I'd have to boot into XP to find out with the device manager.  Is Ubuntu supposed to load the touchpad by default?  Because mine never worked and I have to use an external mouse.

---

### Post by dchen37 on 2007-06-16
It looks like I have both versions installed but it's using 2.5.1-0ubuntu1.  If I try to go to package -> force version from the menu it threatens to remove a bunch of programs that are installed such as alsa-utils, amarok....  Should I go ahead and do it anyways?

---

### Post by 5-HT on 2007-06-17
> **dchen37 said:**
> It looks like I have both versions installed but it's using 2.5.1-0ubuntu1.  If I try to go to package -> force version from the menu it threatens to remove a bunch of programs that are installed such as alsa-utils, amarok....  Should I go ahead and do it anyways?

The errors are likely due to the packages having the same name. If you remove your current 2.5.1-0ubuntu1 python, how many packages want to get removed? One way would be to uninstall your current python, let those other packages go, install 2.5.1~rc1-0ubuntu3, and reinstall the packages that were removed.

Have you tried to force the install of 2.5.1~rc1-0ubuntu3 (apt-get -f install ...)? It can be dangerous but you can simulate the operation beforehand.

I'm not really sure where you got 2.5.1-0ubuntu1 from. Not currently running Ubuntu at the moment, but looking at packages.ubuntu.com, feisty's package seems to be the release candidate one.


For the touchpad:
do you have the synaptics module (driver) installed (xserver-xorg-input-synaptics) and running in the kernel? After that it should only be a matter of setting up /etc/X11/xorg.conf to use it (that should be done by default on the install though, has for me ever since Warty).
Here's the relevant section from my xorg.conf
```
Section "InputDevice"
    Identifier    "Touchpad"
    Driver        "synaptics"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option         "SHMConfig"        "on"   #to allow synclient to monitor/change touchpad settings
    Option        "MinSpeed"        "0.8" 
    Option        "MaxSpeed"        "1.4" 
    Option        "AccelFactor"        "0.1" 
    Option        "RightEdge"        "950"
    Option        "LeftEdge"        "120"
    Option        "TopEdge"        "130"
    Option        "BottomEdge"        "700"
   #Option         "CircularScrolling"     "1"
   #Option         "CircScrollDelta"       "0.1"
   #Option         "CircScrollTrigger"     "2"
    Option            "VertScrollDelta"       "2"
    Option          "HorizScrollDelta"      "2"

EndSection
```**Note that all those 'Option' lines are not necessary, they're just the settings that I like to use for my Alps touchpad (uses the synaptics driver but has different resolutions so the settings may not work well for you, you can omit including all the options).

You'll also need to include the touchpad in the following section. Don't delete anything already there, just add the reference to the touchpad if it's lacking:
```
Section "ServerLayout"
     InputDevice    "Touchpad"    "AlwaysCore"
EndSection
```***Note that I've changed the Identifier to "Touchpad", your identifier may be different. All that matters is that the identifier in the "InputDevice" for the touchpad matches that in the "ServerLayout" section.


If that still doesn't work, you may need to adjust the 'device'. I can provide information on that if it comes to it, but hopefully it won't.

---

### Post by dchen37 on 2007-06-20
Thanks for the help.  I apt-get install -f didn't work (since it was already installed).  I wasn't able to force a different version either because it wouldn't let me remove certain programs.  I didn't try getting the touchpad to work but my new laptop should be coming tomorrow by mail so I'll just start over again.

---

### Post by realvz on 2007-08-17
I have the same problem....i am tryin to install python-dev and i get the followin error....any help is appreciated.

Depends: python (=2.5.1~rc1-0ubuntu3) but 2.5.1-0ubuntu3 is to be installed

---


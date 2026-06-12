---
title: "Changing monitors-- MAJOR COMPLAINT"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-01-12
I have a MAJOR PROBLEM.
I have been playing with Ubuntu, and likeed it so much that I have replaced the lousy, small monitor I used for testing it with a larger, much better one (Dell/Sony).  XP took it without a hitch, giving me much needed 1600X1200 resolution.  Ubuntu (6.10) seems unable to deal with it.  xorg is not configured correctly.  Re-running the nice ENVY script, which installed the Nvidia drivers initially, did not help at all.  Uninstalling the driver ran into some trouble (I was told to switch to level 3 instead of 1), and back out of the unistallation.  
I would like to continue to use UBUNTU, but I simply do not know how to tell it that I am giving it a much nicer monitor.  
Can anyone help, avoiding all Linux-specific acronyms? I can edit the xorg.conf file, but posts here suggest that that way madness lies. I am running now in "recovery mode", so what I need are command line suggestions.
Thanks,

---

### Post by venik212 on 2007-01-12
Some more info: 
The log file tells me that I have an "API mismatch: the NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9631.  Please make sure that the kernel module and all NVIDIA driver components have the same version".
That sounds like sound advice, but I have no idea how to do that.  Where do I change things?  I thought I had the latest NVIDIA driver...

---

### Post by Tomosaur on 2007-01-12
Ok well first of all - you don't need to replace video drivers when you switch the monitor (except in some very extreme circumstances, but usually only on older machines'.

===================================
The nVidia problem:
In recovery mode, try typing:
```

nvidia-xconfig

```
Hopefully it will fix itself, but it may not, this is just a suggestion. You should do this BEFORE setting the new resolution. This may be completely incorrect, or it may work first time, it's just something you may want to try.
==================================

Anyway, what you need to do is boot into recovery mode, and type:
```

nano /etc/X11/xorg.conf

```

Near the bottom of your file, you should see something which looks like this (yours will be slightly different):
```

Section "Screen"

# Enable 32-bit ARGB GLX Visuals
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "RM170"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "TripleBuffer" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

The lines which say 'Modes' are the different resolutions currently available. The line which says DefaultDepth (near the top of this section) is your current depth. You need to find the subsection with that Depth (ie, in my case, 24), then add your desired resolution to the front of the list. Eg, you would change the Modes line to:
```

Modes     "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"

```
Once you've done that, hit Ctrl+x and press enter. Next time you reboot, the machine will TRY to use your new resolution. If it fails, it will try the next one, etc etc.

---

### Post by venik212 on 2007-01-12
Thanks for trying.  None of that worked (nvidia-xconfig returned: No such command...), but I solved my problem.
I used a LiveCD with the new monitor, copied the xorg.conf from that configoration to the old installation, and rebooted.  ALl is well, and Ubuntu reigns again.
However, it is ridiculous to expect people to go through this when they change a monitor.  I expect that the same will face me should I change a mouse, sound card, or any other common piece of hardware.  Linux will never get out of its niche until this is faced and solved.  As I mentioned elsewhere, XP did not even hiccup when I changed the monitor-- it simply used it, with no help from me.

---

### Post by blackened on 2007-01-12
AFAIK problems like these are one of the largest areas of focus being addressed in the next major xorg release.

---

### Post by venik212 on 2007-01-12
Of course, it also wiped out the sounds from my machine... ;-(((((((((((((((((((((

---

### Post by venik212 on 2007-01-12
Can someone please tell me how to restore the sounds to my system?  They were all wiped out when I tried to plug in the larger monitor.  I did several things in trying to get the larger monitor to worK Re-ran the ENVY script (to reinstall and uninstall the NVIDIA driver), and overwrote the xorg.conf I had with the one from the LiveCD.
Anyway, good graphics with no sounds is NOT what I wanted...
Thanks for any help.

---

### Post by bscbrit on 2007-01-12
Have you tried reconfiguring the system to match your new monitor?

sudo dpkg-reconfigure xorg-server

Accept the defaults if you do not know the answer to a question.  Ensure that you select the screen resolutions that you expect to see (and check that the monitor is actually capable of producing them).

---

### Post by bodhi.zazen on 2007-01-12
> **venik212 said:**
> Can someone please tell me how to restore the sounds to my system?  They were all wiped out when I tried to plug in the larger monitor.  I did several things in trying to get the larger monitor to worK Re-ran the ENVY script (to reinstall and uninstall the NVIDIA driver), and overwrote the xorg.conf I had with the one from the LiveCD.
Anyway, good graphics with no sounds is NOT what I wanted...
Thanks for any help.

LOL venik212

Next time with the nvidia thing, try typing nvidia-settings in a terminal and let the nvidia gui do all the work.

also, back up your working xorg.conf

Don't know about the sound. Not to ask the obvious, but you did not accidentally disconnect you speakers when you changed monitors it trust :)

What sound card ?

when I am having sound problems I use alsamixer. It may not be pretty, but it works ....

In a termainal type alsamixer

If you have more then one card, numbering starts with 0 so the second card is 1 :-s

At any rate, for the second card, 

alsamixer -c 1

HTH

---

### Post by venik212 on 2007-01-12
Apparently, in order for the nvidia-settings to work (in the terminal), you have to have the correct driver installed, which I am not sure I do.  In any event, typing it into the terminal does not do it.
Sound problem solved-- my fault.

---

### Post by Delkster on 2007-01-12
> **venik212 said:**
> However, it is ridiculous to expect people to go through this when they change a monitor.
Yeah, manually configuring X Window System (the technical base of the graphical subsystem) is a pain, and it's not done automatically on every boot so after changing you graphics card or monitor you need to at least trigger the auto-detection again manually.

> I expect that the same will face me should I change a mouse, sound card, or any other common piece of hardware.
Actually this isn't true. Most devices (save for those that the X Window System needs to configure) are automatically detected on every boot. Even most drivers aren't "installed" and "uninstalled" -- they just exist and are used when a device that needs them is detected (and stay out of the way when they aren't needed). This works quite nicely.

The graphics card and the monitor are exceptions, and to some extent perhaps the mouse (mostly when it comes to using the extra buttons on mice with a gazillion buttons).

I'm glad to hear that you got the graphics problem solved. For future reference hopefully it won't be needed with future Ubuntu releases!), the first thing I'd try after changing the monitor would be to reconfigure the xserver-xorg package. Start Synaptic, search for the package, click on the package name in the list and select Package > Configure, and answer the questions, particularly the ones about the video driver if you're changing the graphics card and about the resolutions or display modes if you're changing the monitor.

That can also be done on the command line (useful if the graphical system fails to start altogether) with the command "sudo dpkg-reconfigure xserver-xorg".

---

### Post by Delkster on 2007-01-12
> **venik212 said:**
> Some more info: 
The log file tells me that I have an "API mismatch: the NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9631.

Do you still have this problem? To me it sounds like the kernel module is from the NVidia driver package that ships with Ubuntu and the X module is from a newer NVidia release, possibly one that you've manually installed. Have you tried uninstalling the NVidia driver and, if you really want the latest release over the one that comes with Ubuntu, reinstalling the latest driver from NVidia?

I'd keep with the driver that comes with Ubuntu unless you actually need the latest driver, though, because it's less of a hassle. Actually I think the problem may have been caused by a recent kernel update from Ubuntu. With those updates, the drivers that come with Ubuntu are also reinstalled, so that may have overwritten your more recent NVidia module with the Ubuntu-shipped one, which has caused the version conflict. This is mere speculation but it may well be the reason.

If you decide to use an NVidia-provided driver that you install manually, you should uninstall the linux-restricted-modules packages from your system so that possible updates to those don't overwrite your more recent module. Sometimes you might still need to reinstall the driver after a kernel update, though.

None of this mess is there if you use the Ubuntu-shipped driver.

---

### Post by bodhi.zazen on 2007-01-12
> **Delkster said:**
> None of this mess is there if you use the Ubuntu-shipped driver.

Or use the envy script ...

then the nvidia driver is updated both as they become available and with kernel updates :)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)



From CLI:

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb

sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb

```

---

### Post by MasterOfDisaster on 2007-01-12
> **venik212 said:**
> Some more info: 
The log file tells me that I have an "API mismatch: the NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9631.  Please make sure that the kernel module and all NVIDIA driver components have the same version".


Because you are not using the standard driver in the repositories, you have to reinstall nvidia-kernel-common.  Should solve that error message.

Cheers

---

### Post by venik212 on 2007-01-13
That is precisely my point: All I did was change the monitor.  Ubuntu should have used whatever driver was appropriate (as Windows did).  I should not have had to do anything fancy.
How do I tell it to use any particular driver from the repositories?

---


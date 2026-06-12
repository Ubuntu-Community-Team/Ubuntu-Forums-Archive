---
title: "GNOME Resolution problems fixed by XFCE"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by charles.davidson@att.net on 2007-04-17
Hi all,

I'm new to building computers and using linux but I have done the one and am attempting the other.  I have a screen resolution problem that is vexing me.  Initially I couldn't get anything higher than 1024x768 on my widescreen monitor capable of 1680x1050.  I'm running Edgy.

However, I read a few posts and changed the "vesa" driver to "nv" in xorg.conf which got me as high as 1280x800.  (I have an ASUS M2NPV-VM motherboard with integrated nVidia 6150 chipset).  Read a few more posts and installed the binary nvidia driver from nvidia-glx.  

At first I thought this solved the problem as my monitor confirmed that the login screen  was running at 1680x1050.  However, after logging in GNOME would only run at 1440x900.  I tried a bunch of different changes to xorg.conf adding a modeline for the specific resolution and refresh rate, but no luck.  Then I installed Xfce and have absolutely no resolution problems.

Anyone have any insights on how I might get gnome gnome to support my full resolution?

Two more strange symptoms: (1) was that the gnome menu item for changing the screen resolution settings never displayed options higher than 1024x768 or 1280x1024 even when the monitor was confirming that it was receiving 1440x900.  The equivalent tool in Xfce shows all the valid resolutions listed in my xorg.conf file.  (2) is that in some of the incarnations of the xorg.conf file I had tried various refresh rates that were within the spec range of my monitor, but the monitor never reported a change in these values.

Thanks in advance for any tips!  So far I'm really enjoying ubuntu linux.

Charlie

---

### Post by RedSquirrel on 2007-04-17
I don't have any specific tips for GNOME since I don't use it anymore.

In terms of getting your modelines to work, you have to make sure that the "label" of the modeline and the first entry on your Modes line match. Here's mine:

In the *Monitor* section:

```
Modeline [COLOR=Red]"1280x1024_60.00"[/COLOR]  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
```
In the *Screen* section:

```
        SubSection "Display"
                Depth           24
                Modes           [COLOR=Red]"1280x1024_60.00"[/COLOR]
        EndSubSection

```You may have already done that properly, but it's a fairly common mistake so I thought I'd mention it.

And of course your monitor has to support the refresh rate you're trying to set.

[This guide]("http://ubuntuforums.org/showthread.php?p=454217") is helpful in terms of general resolution issues.

---

### Post by charles.davidson@att.net on 2007-04-18
Thanks for the reply, Red.  Unfortunately for me, my modeline matches the modes string in the display subsection of xorg.conf, and both horizontal and vertical refresh rates are within the proper range of the monitor, based on the specs from the manufacturer's site.

Is there any reason why GNOME and Xfce would produce different resolution behavior?  They're both just a front-end to X, yes?

Thanks also for the link to the post on resolution issues.  That's one I have seen before, but maybe it is worth a second look.

Anyone else seen these troubles?  I'm using a ViewSonic 20" Widescreen monitor, ASUS M2NPV-VM mobo (BIOS version 0705).

Charlie

---

### Post by RedSquirrel on 2007-04-19
Well, good job on getting the modeline setup. ;)

GNOME and Xfce seem to do some interesting (frustrating?) things when it comes to resolutions.

When I installed Xfce, it had a rather lengthy list of resolutions and I'm not even sure they were all supported by my monitor. For that WM, I used the "Default" setting for the resolution which grabs the one in xorg.conf.

When I used GNOME (briefly), I had a monitor @ 1024x768, which GNOME had no trouble with. Setting up widescreen resolutions seems to an adventure, though. I think there is a way to tell GNOME which resolution to use, but I don't recall it. I never had to tinker with that myself and now I don't even have GNOME installed. I use Fluxbox, which takes the resolution out of xorg.conf. :)

Sorry I can't be more helpful. Good luck.

---

### Post by counterpoint on 2007-06-03
I'm having a somewhat similar problem, and would be very grateful for any suggestions.  Running Ubuntu 7.04 on Asus MN2PV-VM with onboard Geforce 6150.  New monitor is NEC LCD2170NX, capable of 1600x1200 at 60 Hz (which appears to be well within the Geforce spec).  I got into a mess with various experiments, so did a fresh install, then replace the nv driver by using the package manager to install nvidia-glx (currently 1.0.9631).

Although the xorg.conf was generated with a whole range of resolutions up to 1920x1440, the Gnome screen resolution selector resoutely refuses to offer anything better than 1400x1050 at 57Hz.  There is no modeline at all in the xorg.conf - is that a problem?  The activation of the nvidia driver did not work from the suggested enable command, giving an error that said simply edit xorg.conf to change nv to nvidia - which I did.  Is that connected with the lack of modeline?  Or do I need something specific to the NEC for the terminal section?  If so, what is the source for the information?  The NEC was used for the fresh Ubuntu install.

As you'll gather, I'm getting a bit lost here, not being any kind of expert on either hardware or system software :)

---


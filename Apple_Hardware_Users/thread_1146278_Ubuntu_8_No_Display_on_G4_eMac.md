---
title: "Ubuntu 8 No Display on G4 eMac"
date: 2009-05-02
forum: Apple Hardware Users
---

### Post by CharlesParish on 2009-05-02
My eMac after installing Ubuntu successfully when allowed to boot untouched it will load the Ubuntu loading screen all the way through and then the screen will flash and go black. I can hear the computer still running in the background. I have tried.

```
Linux video=ifonly

and

Linux video=ifonly nosplash
```Any ideas?

EDIT: I can press CTRL+OPT+F1 and I go to a terminal that asks me to log in, but my password that I set up during install doesn't work. I tried to reinstall with a new password and it still doesn't work.

---

### Post by stream303 on 2009-05-02
This may be a typo - you probably meant "ofonly" instead of "ifonly".

And all that will do is get you past the splash screen, but I recommend it even though your system seems to get past it, whereas with others, the splash screen can lock up the drivers.  So try "ofonly".

Emacs have very specific refresh rates that need to be manually configured in /etc/X11/xorg.conf.  For example, you'll need to manually edit that file, and change your refresh rates for the emac:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	[b]HorizSync	71-73
	VertRefresh	70-140[/b]
EndSection
```

(NOTE: G3 iMac lurkers:  G3 iMacs need a horizontal of 58-62 and a vertical of 75-117 - these G4 eMac values above won't work on iMacs. :) )

Which Emac are you running?  If you are running one of the earlier ones with Nvidia graphics, this may be all you need.  If you are using a later one with ATI graphics, there will be more configuration needed:

[http://www.everymac.com/systems/apple/emac/index-emac.html](http://www.everymac.com/systems/apple/emac/index-emac.html)

I'm assuming you are running / installing 9.04 Jaunty now that you mention those password problems.  Are you upgrading, or doing a fresh-install?  Most of the reports that I've seen regarding bad passwords involve an upgrade, but perhaps this is also happening on totally fresh wipe-the-drive clean installs?

If you are in a bind, you can install 8.04 LTS, but will still have to manually configure /etc/X11/xorg.conf specific to the G4 eMac requirements, but won't run into that password issue.

From what I understand, this password issue is not ppc-specific, and the problem is being worked on - although it can be a catch-22 if you can't logon to get the updates for the fix! :)

So, to help out, what exact machine are you running, are you running Ubuntu or Kubuntu or Xubuntu, and I take it you are doing a real fresh install, and not an upgrade?

When these are known, maybe we can get you over the initial hurdle.

---

### Post by CharlesParish on 2009-05-02
> **stream303 said:**
> This may be a typo - you probably meant "ofonly" instead of "ifonly".

And all that will do is get you past the splash screen, but I recommend it even though your system seems to get past it, whereas with others, the splash screen can lock up the drivers.  So try "ofonly".

Emacs have very specific refresh rates that need to be manually configured in /etc/X11/xorg.conf.  For example, you'll need to manually edit that file, and change your refresh rates for the emac:

```
Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    [B]HorizSync    71-73
    VertRefresh    70-140[/B]
EndSection
```(NOTE: G3 iMac lurkers:  G3 iMacs need a horizontal of 58-62 and a vertical of 75-117 - these G4 eMac values above won't work on iMacs. :) )

Which Emac are you running?  If you are running one of the earlier ones with Nvidia graphics, this may be all you need.  If you are using a later one with ATI graphics, there will be more configuration needed:

[http://www.everymac.com/systems/apple/emac/index-emac.html](http://www.everymac.com/systems/apple/emac/index-emac.html)

I'm assuming you are running / installing 9.04 Jaunty now that you mention those password problems.  Are you upgrading, or doing a fresh-install?  Most of the reports that I've seen regarding bad passwords involve an upgrade, but perhaps this is also happening on totally fresh wipe-the-drive clean installs?

If you are in a bind, you can install 8.04 LTS, but will still have to manually configure /etc/X11/xorg.conf specific to the G4 eMac requirements, but won't run into that password issue.

From what I understand, this password issue is not ppc-specific, and the problem is being worked on - although it can be a catch-22 if you can't logon to get the updates for the fix! :)

So, to help out, what exact machine are you running, are you running Ubuntu or Kubuntu or Xubuntu, and I take it you are doing a real fresh install, and not an upgrade?

When these are known, maybe we can get you over the initial hurdle.

Here's the machine I am working on [http://www.everymac.com/systems/apple/emac/stats/emac_1.25.html](http://www.everymac.com/systems/apple/emac/stats/emac_1.25.html)

What's a Jaunty? I just used the basic install of Ubuntu and I'm working through it. Is there any way to reconfigure that file without logging in? Can I edit it while installing the system? Where can I find the LTS that manually configs? Sorry for all the questions. I'm new to the whole linux thing and would like to get this computer back up and running.

I appreciate your effort
-Charlie

---

### Post by stream303 on 2009-05-03
No sweat - Jaunty, Hardy, Intrepid, etc are nicknames for the releases like 9.04, 8.04, 8.10 etc.  Keeps us from sounding like robots when discussing them. :)

I hope we can get your machine up and running with Ubuntu - but just know up front that Apple PPC with any Linux distro is not the best choice for a beginner due to the fact that Apple hardware doesn't always provide the right values to the Linux installation routines - which means you'll be diving head first into manually configuring text files, learning editors, and whatnot.  If that's not a problem for you, let's do it!

[http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

Thing is, this may take a few days or weeks provided you haven't dumped it in the trash. :)

Ultimately, just be sure not to judge how Ubuntu or any other Linux distro works based on how hard it may be to install on Apple hardware.  It isn't Linux' fault, but the lack of documentation from Apple to the Linux devs.  They aren't exactly excited about having users run anything but OSX. :)

Even in the end with a successful Linux install, you won't have any flash or 3D video, no sleep or hibernation usually, and even more little issues may appear.  So while you may end up with a nice general-purpose Linux box on PPC, it may not fit your needs in the end.

In that case, I have no qualms about recommending a retail install of OSX to get that box back into shape if need be.

---

### Post by apa240 on 2009-05-25
[http://ubuntuforums.org/showthread.php?t=964032&page=3]("http://ubuntuforums.org/showthread.php?t=964032&page=3")

That worked for me.

If you can, download 9.04 because it should work without any problems.

---


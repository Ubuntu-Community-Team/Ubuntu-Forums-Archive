---
title: "xorg in Trusty 14.04 in Parallels VM on MacBookPro 15inch does not recognise Retina"
date: 2014-04-20
forum: Apple Hardware Users
---

### Post by Rehd on 2014-04-20
Background:
Xubuntu Saucy 13.10 runs flawless in a Parallels Desktop 9 virtual machine on a Retina, 15-inch, Late 2013, MacBook Pro.

The only thing required was changing the DPI to 220 in the settings dialogue and fix the DPI in the Firefox about:config. Window borders, and mouse pointer  are still too small, but I do not bother so much, since most of my time is spent in Emacs, Vi, Terminal and Firefox, so everything just fine for me.

BUT: any version of Trusty (Xubuntu, Ubuntu, Kubuntu) since the daily builds after beta run 800x600 pixels and no way around it for me X11-illiterate. I know my way around xrandr and found some posts pointing out tweaks of adding and setting modes in connection with a full install on a Retina MacBookPro. They did not work out in the virtual machine. I spend some hours googling around the topic to no avail and learning the whole X server system and configuration procedures seem a bit of an overkill.

Can anybody point out some basic points.

Specs:
[LIST]
[*]Late 2013 MacBookPro 15inch Retina
[*]OS X 10.9 host OS
[*]Parallels Desktop VM Build 9.0.24229 for Mac
[*]Kubuntu 14.04 Trusty Tahr right now, but the issue is with underlying X, since it is the same on all *buntus
[*]
[/LIST]

```

rforge@P9:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 0mm x 0mm
   800x600        75.0* 

```

This is everything. Note that the very well working Xubuntu 13.10 also complains about "Failed to get size of gamma for output default" but has all the correct resolution modes listed.

The graphics driver of the VM after the "Parallel Tools" guest addition install is listed, but the xorg configuration seems to fail.

```

rforge@P9:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Parallels, Inc. Accelerated Virtual Video Adapter

```

Any help appreciated,
thanks,
Reinhard

---

### Post by bapoumba on 2014-04-20
Moved to Apple Users.

---

### Post by Quackers on 2014-04-20
I use VMWare Fusion rather than Parallels. In Fusion, after installing Trusty, I needed to re-install/update VMWare tools. Is there something similar in Parallels?

---

### Post by Rehd on 2014-04-26
Yes, you have to install parallels-tools, like VMWare tools or VirtualBox's Guest Additions. It is pretty much automatized in Parallels, but to no avail.

It seems that maybe it has to do with an Parallels upgrade and the graphics driver is broken for Linux or something.

As I mentioned, I have no knowledge about the hardware abstraction/ driver side of Linux/Xorg, so any general hint about debugging an Xorg graphics problem would be very much appretiated.

Therefor I did not post in Apple Users. My general impression is that forums/community/support sucks when it come to both MacOS and of course Windows.
Note explicitly: I am not referring to the user base as persons, I am sure they are as idealistic (especially the *nix on Mac users) as any open source advocates. I am referring to my personal experience about both width and depth of information/documentation in the public space.

Just to give an example: I am looking for a way to start an ISO image in Parallels, without creating a virtual harddisk. Very trivial and straightforward and well documented in VB. Nothing in the forums or documentation for Parallels - no answer on the forum pages.

Xubuntu 12.04 is running pretty well on my MacBook and I am doing all my work inside it. Then I still have OS X for entertainment (Netflix, e.g. has no Linux port). I am using it only for occasional gaming and entertainment. So it is basically a successful setup. But there always stays some bitter taste and I always gravitate back to a (Windows) PC and wipe the harddisk and have netflix evtl in a VB Windows XP machine.

A bit length and late reply. My workload is quite intense right now, and my Linux VM has to be working without to much fuzz.

Any help/hints/tips for debugging Xorg would be very much appretiated, such that I can give specific information to the Parallels Support / Bugs department..

---

### Post by diff111 on 2014-04-29
I had the same problem (display resolution stuck at 800x600) in Kubuntu 14.04 on a Macbook Air with Parallels Desktop and fixed it in the following way. In the /etc/X11 folder there is a backup xorg.conf file named something like xorg.conf.XXXXXXXX (where XXXXXXXX is the creation date). The trick is to rename it as xorg.conf:

sudo cp /etc/X11/xorg.conf.XXXXXXXX /etc/X11/xorg.conf

and reboot. Hope this helps.

---

### Post by Brandon_Arrendondo on 2014-04-29
Thank you for your solution.  I just did a dist-upgrade to 14.04 and was having the exact same issue on my Mac running XUbuntu in Parallels.  Sure enough - I copied /etc/X11/xorg.conf.dist-upgrade-201404291005 to /etc/X11/xorg.conf and it fixed the issue.  Thanks again!

---

### Post by Rehd on 2014-05-05
Thanks diff111 for your solution. It works!

This is another example why there is no going back from open source. Every problem one encounters as a beginner has already been solved by someone reading the forums. Very kind indeed. Sorry for the late reply, but as I said, I am under press to finish some projects and cannot use to much time to tinker with my production system.

Thanks to you, I can now upgrade to Trusty. Excellent.

---

### Post by David_Howard on 2014-05-09
@dif111 - I also found the suggested fix to work perfectly - thanks much!

---


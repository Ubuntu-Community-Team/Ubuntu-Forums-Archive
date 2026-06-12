---
title: "BIOS not booting from cd"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by bibby on 2006-05-03
BIOS not booting from cd
     ... at least that's one problem.

I'm a total noob (done some ssh,scp in Cygwin, but no distros).
I tried replacing WinXP with Debian, and it didn't go very well.
More on that below, but right now, this is my conern.

I got a Ubuntu CD, and want to get it loaded instead.
BIOS is set to boot from cdrom 1st, and it looks like it tries, but after a short time grub takes over and asks me to pick a kernel.  
How can I get the cd to start instead?

-----------
--------
-----:-k 
-- Debian woes:
 I don't know what I need / dont need ,  but I've never seen more than the commandline.
 startx tells me theres no /ect/X11/X*somethin  ,
 gnome-session gives a GTK warning
I got nothing.

 I started out with the 180MB cd, and used aptitude to get a bunch of other stuff, but I suppose not enough of what I need and too much of what I do not (typical windows move)

Forgive me for branching my post but
alt1: What can I do to save this install ?
alt2: What can I do to scrap it? (just BIOS and I for a chat about Ubuntu)

Thanks for reading.
More so for a reply!
~!b

---

### Post by yager on 2006-05-03
[QUOTE=bibby]I got a Ubuntu CD, and want to get it loaded instead.
BIOS is set to boot from cdrom 1st, and it looks like it tries, but after a short time grub takes over and asks me to pick a kernel.[/QUOTE]

What was your source for the Ubuntu disk?  Did you download the ISO file and then burn it as an ISO file to a new CD?  If the file was burned to the CD as a Data CD, it will not boot as it is not a bootable image.

If you still have access to a Windows computer, you can check to see if the CD has anything on it as well.  When inserted, it should autoplay a browser window that lets you install a couple of different open source apps.

As another test, do you have a recovery disk for windows or some other bootable CD available?  Maybe Knoppix?  If so, see if you can boot from one of them.  If so, then it has to be a bad Ubuntu disk that you are dealing with.  If the problem is present with those disks as well it has to be a configuration or hardware problem.

---

### Post by Mustard on 2006-05-03
With the Debian issue, you probably just need to apt-get some more stuff to get X working.  I've been doing the same thing with a base install from the 180mb CD and then using netinstall for the rest.  Basically you can use the apt-cache search function and apt-cache show function to look for the packages you need to install.  The packages would probably be called x-window-system-core , x-window-system, x11-common.  I have no idea really, but I just stumbled my way through installing stuff related to the x server until startx worked.  I installed xfce4 and used the gdm login prompt to login to xfce.

Some examples of my searches...

```
root@slave:/# apt-cache search xserver
isdnutils - Most important ISDN-related packages and utilities
isdnutils-base - ISDN utilities, the basic (minimal) set
isdnvboxclient - ISDN answering machine, client
isdnvboxserver - ISDN answering machine, server
libxcomposite1 - X off-screen compositing library
libxdamage1 - X region 'damage' library
mgapdesk - X configuration tool for Matrox video card
skippy - full-screen X11 task/window switcher, similar to OSX Expose
tightvncserver - virtual network computing server software
ts10 - Emulators for PDP-10, PDP-11, VAX
ucspi-unix - UNIX-domain socket client-server command-line tools
vnc4server - Virtual network computing server software
vncserver - Virtual network computing server software
wmcb - Dockapp that displays the cut buffer content
x11-common - X Window System (X.Org) infrastructure
xbase-clients - miscellaneous X clients
xdebconfigurator - A script used with debconf to autoconfigure xserver-xfree86
xlibmesa-dri - Mesa 3D graphics library modules [X.Org]
xserver-common - files and utilities common to all X servers
xserver-xfree86 - transitional package for moving from xfree86 to X.Org
xserver-xorg - the X.Org X server
xserver-xorg-dbg - debugging symbols for the X.Org X server
xserver-xorg-input-citron - X.Org X server -- Citron input driver
xserver-xorg-input-evdev - X.Org X server -- evdev input driver
xserver-xorg-input-kbd - X.Org X server -- keyboard input driver
xserver-xorg-input-mouse - X.Org X server -- mouse input driver
xserver-xorg-video-apm - X.Org X server -- APM display driver
xserver-xorg-video-ark - X.Org X server -- ark display driver
xserver-xorg-video-ati - X.Org X server -- ATI display driver
xserver-xorg-video-chips - X.Org X server -- Chips display driver
xserver-xorg-video-cirrus - X.Org X server -- Cirrus display driver
xserver-xorg-video-cyrix - X.Org X server -- Cyrix display driver
xserver-xorg-video-dummy - X.Org X server -- dummy display driver
xserver-xorg-video-fbdev - X.Org X server -- fbdev display driver
xserver-xorg-video-i128 - X.Org X server -- i128 display driver
xserver-xorg-video-i740 - X.Org X server -- i740 display driver
xserver-xorg-video-i810 - X.Org X server -- Intel i8xx, i9xx display driver
xserver-xorg-video-imstt - X.Org X server -- IMSTT display driver
xserver-xorg-video-mga - X.Org X server -- MGA display driver
xserver-xorg-video-neomagic - X.Org X server -- Neomagic display driver
xserver-xorg-video-newport - X.Org X server -- Newport display driver
xserver-xorg-video-nsc - X.Org X server -- NSC display driver
xserver-xorg-video-nv - X.Org X server -- NV display driver
xserver-xorg-video-rendition - X.Org X server -- Rendition display driver
xserver-xorg-video-s3 - X.Org X server -- legacy S3 display driver
xserver-xorg-video-s3virge - X.Org X server -- S3 ViRGE display driver
xserver-xorg-video-savage - X.Org X server -- Savage display driver
xserver-xorg-video-siliconmotion - X.Org X server -- SiliconMotion display driver
xserver-xorg-video-sis - X.Org X server -- SiS display driver
xserver-xorg-video-sisusb - X.Org X server -- SiS USB display driver
xserver-xorg-video-tdfx - X.Org X server -- tdfx display driver
xserver-xorg-video-tga - X.Org X server -- TGA display driver
xserver-xorg-video-trident - X.Org X server -- Trident display driver
xserver-xorg-video-tseng - X.Org X server -- Tseng display driver
xserver-xorg-video-vesa - X.Org X server -- VESA display driver
xserver-xorg-video-vga - X.Org X server -- VGA display driver
xserver-xorg-video-via - X.Org X server -- VIA display driver
xserver-xorg-video-vmware - X.Org X server -- VMware display driver
xserver-xorg-video-voodoo - X.Org X server -- Voodoo display driver

```

From the above I figured I probably needed x11-common so I did this...

```
root@slave:/# apt-cache show x11-common
Package: x11-common
Priority: optional
Section: x11
Installed-Size: 1608
Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: all
Source: xorg-x11
Version: 6.9.0.dfsg.1-6
Replaces: xfree86-common (<< 6.8.0), x-common
Provides: xfree86-common
Depends: debconf (>= 1.2.9) | debconf-2.0, debianutils (>= 1.13), lsb-base (>= 3.0-1)
 
Conflicts: task-x-window-system-core, task-x-window-system, xfree86-common (<< 6.8.0), x-common
Filename: pool/main/x/xorg-x11/x11-common_6.9.0.dfsg.1-6_all.deb
Size: 1124704
MD5sum: 9d5b7995a8b3a59552fb8faca255e0c0
Description: X Window System (X.Org) infrastructure
 x11-common contains the filesystem infrastructure required for further
 installation of the X Window System in any configuration.
 .
 Those wishing an X server only (with remote font services and clients) will
 also require the xserver-common package and an X server package (most
 likely xserver-xorg).
 .
 The counterpart to the above configuration is a machine with the X libraries,
 xbase-clients, a window manager, some X font packages, and likely many more
 client packages.
 .
 Those who desire a standalone X workstation (and/or are fuzzy on the concepts
 of X servers and X clients) will require both of the above sets of packages.
 For convenience, the "x-window-system" metapackage will include everything
 that is required for a standalone X workstation.
 .
 A number of terms are used to refer to the X Window System, including "X", "X
 Version 11", "X11", "X11R6", and "X11R6.8".  The version of X used in Debian
 is derived from the version released by the X.Org Foundation, and is thus
 often also referred to as "X.Org".  All of the preceding quoted terms are
 functionally interchangeable in an Debian system.
 .
 Until recently, Debian shipped an X implementation released by The XFree86
 Project, Inc. (aka "XFree86").  The X.Org implementation is derived from the
 XFree86 implementation previously shipped, and is generally considered to be
 the standard implementation by vendors and distributors.
 .
 Still confused?  Install this package and then read the files in
 /usr/share/doc/x11-common/ for assistance.

```

Now in the suggested packages it had *Suggests: x-window-system-core | x-window-system*, so I installed the suggested packages as well.

Basically if you don't have a clue like me, you just keep using apt-cache search and apt-cache show until you figure out which packages all work together to get the x server running.  I know its pretty vague, but I've only just tried some of this stuff out myself, so I'm still learning. :)

---

### Post by bibby on 2006-05-03
I was able to scrap my install using fdisk.
The CD must be bad, or at least not intended for this purpose, because the boot from cdrom failed.

This windows machine I'm using now, ironically, has a broken cd drive. I can check this later in the day at another machine.  --possibly burn new images from the joint were the kids play warcraft. 

In the meantime, I'm using the same the Debian disc and will keep plugging away at packages until the rum puts me to bed. I expect to be no worse off than I was.

x-windows-core I know I had, but others are worth a look.
I thank you both.

---

### Post by Mustard on 2006-05-03
[QUOTE=bibby]I was able to scrap my install using fdisk.
The CD must be bad, or at least not intended for this purpose, because the boot from cdrom failed.

This windows machine I'm using now, ironically, has a broken cd drive. I can check this later in the day at another machine.  --possibly burn new images from the joint were the kids play warcraft. 

In the meantime, I'm using the same the Debian disc and will keep plugging away at packages until the rum puts me to bed. I expect to be no worse off than I was.

x-windows-core I know I had, but others are worth a look.
I thank you both.[/QUOTE]

Keep plugging away, it feels good when it finally all comes together. ;)  It took me two days to get past one problem I had.  I wanted to use XDM to handle the graphical login, and I tried for days to get it to work.  Eventually I compromised and installed the GDM login instead and if worked flawlessly.  The apt-cache show x11-common example I showed above has some good tips in the description.  Including the last line in the description referring to some docs files you can install and then have a read of.

---

### Post by bibby on 2006-05-03
I'm getting there. I realized the second time around that I had made a fundemental mistake with the 'checkboxes' the first time.  Instead of using the spacebar, I hit enter and failed to select Desktop Environment, Web Server, ect.

This install, X wants to run.     ...only it doesn't.

According  to my err msgs,  gdm needs to be reconfigured.
Not knowing how to do that necessarily, I'm off to google some gdm.

---

### Post by Mustard on 2006-05-03
I've become so personally attached to my new debian install, I've been neglecting my Ubuntu installation. :D

I still have a way to go before this new install is up to scratch though.  Just realised today I didnt have a gui text editor installed and found a nice one for xfce called mousepad.

It could be that I installed xfce4 that has made things easier for me, I don't know.  With xfce I ran xfce4_setup (assuming it would help), and then ran startxfce4 to start the xserver. There is a package called configure-debian that might have some use to you.  I'm not sure exactly what it does either but I ran it a few times to see if it could help with anything.

---

### Post by bibby on 2006-05-05
A little work done, so a little update.

I went throught /var/log/Xfree86.0.log
and found that it states
'insufficient memory for mode' for basically all decent display resolutions.
It's also set up with a genereic video card and generic monitor.

My card is a SIS with 64MB RAM. Is there an easy way to change these settings without answering (and possibly bombing) unnecessary questions?

thanks!
~!b

---

### Post by Mustard on 2006-05-05
[QUOTE=bibby]A little work done, so a little update.

I went throught /var/log/Xfree86.0.log
and found that it states
'insufficient memory for mode' for basically all decent display resolutions.
It's also set up with a genereic video card and generic monitor.

My card is a SIS with 64MB RAM. Is there an easy way to change these settings without answering (and possibly bombing) unnecessary questions?

thanks!
~!b[/QUOTE]

I'm familiar with reconfiguring xorg, but I'm not so sure about xfree86.  This might be a question you can ask in #debian on irc.freenode.net

Either that or you can install xorg instead of xfree86. :)

-edit-

I just popped in to #debian and queried the bot about this and this is its reply...

> it has been said that drxx is dpkg-reconfigure xserver-xfree86 [or xserver-xorg if you're using X.org]. Run it as root, and ask about xmd5 if you changed the configuration files yourself.


You could run the above command as often as you like to experiment with different options.  If you get it wrong first time around, try running it again.  Most times you don't need to fill in the blanks, you can just choose the default answer (which may well be leaving a section blank).

---


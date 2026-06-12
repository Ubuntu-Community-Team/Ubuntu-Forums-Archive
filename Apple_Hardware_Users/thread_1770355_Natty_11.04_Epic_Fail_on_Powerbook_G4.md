---
title: "Natty 11.04: Epic Fail on Powerbook G4"
date: 2011-05-29
forum: Apple Hardware Users
---

### Post by serpetiello on 2011-05-29
*Where did I start...*

I have an Apple Powerbook G4 17" Feb'2005 (1.67GHz PPC G4 CPU, 1Gb RAM, 100Gb hdd) at home. Having the infamous "vertical lines" problem, I need to use use an external 1440x900 DVI monitor (same resolution as braindamaged Apple LCD). I also have some USB-serial hardware (weather station, Arduino, etc) and a Nokia N900 configured as a router (this lets me use a fixed IP on the Powerbook).

I had Ubuntu 9.10 running 24h/24 up to yesterday, so I just updated the yaboot.conf in */dev/hda2* (the boot partition) and booted natty off hard disk and USB pendrive (great thing having an yaboot on a bootable partition).

Since Apple separated me from 2900 bucks (ouch!!) six years ago, I don't want to abandon this Powerbook until its very end. But it seems Natty is not a viable option...



*Workaround for "mirror" error...*

Installation of Natty stopped because a "mirror" error. In the syslog messages I found these errors:

```

May 27 21:21:41 ubuntu choose-mirror[32259]: WARNING **: mirror does not support the specified release (natty)
May 27 21:21:42 ubuntu choose-mirror[32259]: DEBUG: command: wget -q http://mirror/ubuntu-ports//dists/natty/Release -O - | grep -E '^(Suite|Codename):'
May 27 21:21:42 ubuntu choose-mirror[32259]: WARNING **: mirror does not support the specified release (natty)

```

Note the mistaken address: I think that some Perl programmer forgot the '$' before 'mirror', and the "mirror" variable does not get expanded ;)

Workaround: just *ping ports.ubuntu.com* and take note of its IP address. Then edit/create the */etc/hosts* file and add this line faking an hostname "mirror", alias for "ports.ubuntu.com", with the actual ports.ubuntu.com address you just found:

```
91.189.92.175 ports.ubuntu.com mirror
```

(change the 91.189.etc with the actual IP you got from "ping").

This way, installation was flawless. The boot completes quickly after the monstruous pre-boot waits (more than 30seconds with black screen, I guess it is due to the two external USB hubs).



*Same old annoying Ubuntu bug...*

By default Ubuntu Gnome installation requires a password after a screen blanking (the default in Power Management preferences is to blank the screen after 15 minutes). Workaround: use these steps (if it does not work, repeat again):

* start gconf-editor
* select apps / gnome-power-manager / lock
* enable "use screensaver settings"
* select apps / gnome-screensaver
* disable "lock enabled"
* select file / quit to exit

Note: verify your screensaver preferences as well.



*First impressions...*

Apparently Ubuntu 11.10 is faster than Ubuntu 9.xx, but I will be able to confirm only when I'll finish installing/configuring tons of stuff (including LyX, requiring by itself more than 400Mb download).

First thing I noticed: the CPU cooler fan works (and works better than it did in OS X, showing now different speeds and only for a few seconds). I wonder how happened my Powerbook is still alive working 24h/24 for more than two years without the fan.

First problem: Unity does not work. This Powerbook sports a 128MB Radeon 9600 2D/3D accelerated videocard. Not only it is insufficient for Unity, but Natty/PPC shows the same old "top stripe" menu Applications-Places-System since ages. Funny, my 11.04/intel on a PC with a GM855 "shared memory" video card (which does not support Unity as well), appears with the newer "stripe" version (where you must click on top-left Ubuntu icon to get apps, places and system menus, and where you get the top menu File-Edit-View-etc saving some vertical space on screen).

Another problem: zooming/unzooming maximized windows will lead sometimes to unrefreshed screen areas (mostly a few pixels large columns on the borders); this did not happen in Ubuntu 9.xx/PPC.



*Powerbook specific things...*

Another annoying problem: I cannot set LCD brightness (having an external DVI display, I do not want the "vertical lines" damaged 17" LCD to be on). This worked flawless on Ubuntu 9.x (just pressed F1 F1 F1 after Ubuntu starts, and the LCD goes off) but now on Ubuntu/PPC 11.04 does not work.

So I installed anything related to "powerbook". First, gtkpbbuttons-gnome and pbbuttonsd; the first complains about some missing */dev/dsp* (huh? why dsp?) the second recognizes other buttons but ignores F1/F2 keys (the ones which should change brightness), even if a Terminal cursor blink shows that the keypress was correctly recognized. The Brightness applet also shows a "not available" icon. The audio volume keys work as expected (but they are managed by Gnome). The F7 key (change display) just flickers the screens (remember that the Powerbook function keys need the Fn key pressed to act as "true F1, true F2 key, etc").

No change after a reboot. When the external DVI display goes in power-saving mode (as commanded by Power Management preferences), the LCD blanks but remains active with maximum brightness. Even selecting 0 on LCD brightness in */etc/pbbuttons.conf* and restarting, nothing changes.

Neither works the dirtiest workaround (start gconf-editor, enter "apps / gnome-settings-daemon / xrandr" and disable "turn-on-laptop-monitor"), so I guess it could be an X11 driver bug/problem. Alas, Gnome Power Management preferences do not allow to set to "Do Nothing" the event "When laptop lid closes". Anyway, closing the lid does not turn off the LCD (arrrgh).

The hdapsd complains about some missing files in the (wasn't it deprecated?) */sys* filesystem and suggests recompiling.

There is still the "split-second display flicker" bug, I think it is not a Powerbook hardware problem but an X11 problem. The display appears to shift to left by one or two pixels for some 0.2-0.4 seconds and then back to normal. That ugly thing happens every time some program uses lots of CPU or draws lots of things on screen. A cold boot is needed to get back to normal but the horrendous phenomenon sooner or later appears again...



*Other hardware issues...*

Duh, another regression: trying to setup external monitor as "desktop extension" instead of "mirror screen" gives out an error: "virtual screen required: 2880x900, max available 1440x1440". I wonder if this is Ubuntu 11.10 or 1.1...!

Bluetooth and Wifi do not work out of the box. Bluetooth appears "disabled"; you click on "enable" but nothing happens. On Ubuntu 9.10 it worked somewhat (I was able to pair devices and exchange files).

The Wifi needs firmware chunks from Broadcom. As usual:
- install b43-fwcutter package
- get and uncompress [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
- enter its "driver" directory
- for a in *.o; do b43-fwcutter -w /lib/firmware $a; done # ignore error messages
- after a reboot wlan appears there but... does not find wifi networks, and if you create a local wifi network other wifi-enabled machines won't see it. Maybe I should try some older firmware (b43legacy).



*Software delusions...*

Yes, Firefox 4.0.1 plays Youtube videos. But not every other software goes OK like Firefox...

Chromium browser not available, maybe its installation will need some hack (but lots of other nice browsers are here: Dooble, Seamonkey, Epiphany, Arora and so on).

Arduino environment install complains about a "non-installable" libtxrx-java package (ouch!): thus it is not installable.

Mplayer not installable: was compiled against a deprecated and non-installable libx264 (funny, its "libx264-dev" package is available); there was a switch from "libx264" to "x264" but Natty/PPC seems not to know ("x264" is installable but "mplayer" requires the old "libx264").

The ssh works but... requires 15-20 seconds for the initial handshaking between two Natty installs (a PPC and an Intel one). Ouch!!! older Ubuntu versions required almost no time!

Evolution 2.32.2 (yes, 11.04/PPC has the old 2.32.2, not 3.xx) moved my *$HOME/.evolution* directory into *$HOME/.local/share/evolution* making me wonder for some minutes where my 3+Gb mail database went. Filters and messages were there, but I had to reconfigure all mail accounts, experiencing a few seconds wait when... clicking on "IMAP" dropdown to select "POP". I didn't consider backupping/restoring because jumping from 2.28 of Karmic to 2.32 of Natty seemed a safe step.

And yes, if you happen to ask *ls -al* in your home, well, you still have that ugly MSDOS-style rubbish *.gvfs* line ("d?????????  ? ?    ?       ?                ? .gvfs"). Real Ubuntu Linux Masters don't do *ls -al* in their home directories, it seems.



*Conclusion (for now)*

All of the "problems" remained the same even after updating/upgrading packages, even with proposed/backports enabled, even after reboots.

Natty 11.04/PPC is still "alpha" quality with a few (but very annoying) bugs. Maybe this is why you can't directly download it in the Ports section.

The execrable "split-second desktop shift" and the "LCD always on (no brightness control)" are sufficient reasons, for me, to go back to Karmic 9.10/PPC and wait some six months hoping that Ocelot/PPC won't need an *"Epic Fail!"* mark.

---

### Post by serpetiello on 2011-05-29
Forgot to say that the */etc/hosts* hack is required both in the Live system before installing packages, and in the installed system. The *apt-get* and Synaptic and Ubuntu Software Center worked well (but -alas!- complained about Mplayer, Arduino, etc).

---

### Post by crispino on 2011-06-21
Hi I was reading this while installing natty on my powerbook 12". Editing the hosts file made me able to finish the installation, but like you I was unable to get the wifi working. I found that installing the source deb firmware-b43-installer from synaptic resolved this problem. After installing the package wifi was up and running within seconds. If now I could only resolve the issues I have related to the powermanagement...

---

### Post by crispino on 2011-06-22
I now managed to install mplayer. I solved the problem with x264/libx264 by installing the libx264 package from 10.10. Downloaded the package and installed with dpkg. I don&#42892;t know if you by now have reverted back to an older version of ubuntu, but I&#42892;ll continue to update this thread if I manage to resolve some of the other issues that you mention (for the comodity of other readers).

---


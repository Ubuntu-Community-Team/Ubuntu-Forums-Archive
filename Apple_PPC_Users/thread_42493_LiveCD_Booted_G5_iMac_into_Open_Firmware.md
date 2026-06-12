---
title: "LiveCD Booted G5 iMac into Open Firmware"
date: 2005-06-17
forum: Apple PPC Users
---

### Post by sgmorr on 2005-06-17
I've successfully downloaded, burned and booted Ubuntu live on my G4 iMac.

However, while visiting my brother, I downloaded and burned the Ubuntu live CD and attempted to boot his G5 iMac with it. It began with a black screen and white type just as it did on my G4. But when it got to the first "stopping point" and asked if I wanted to access "help" or to press "enter" to continue, I pressed "enter" and the G5 then booted into Open Firmware with black type on a white. The keyboard was unresponsive and I could not type "mac-boot" so I had to press the power button and then I booted back into Tiger.

By the way, the G5 has a Bluetooth keyboard and mouse. Does this make any difference? Thanks.

---

### Post by john boyden on 2005-06-29
I got by the white screen problem (Mac G5) by re-booting the live cd,
instead of typing "live" I typed "help" which gave me the option
of other things to type if I pressed tab.  I selected "live-power4"
and Ubuntu booted successfully.  I then encountered another
problem which I havn't been able to solve;  a screen came up which
wanted me so select a language, english was pre-selected but pressing
enter had no effect, the keyboard seemed to be absolutely dead.
If anyone has the solution I'd be glad to know what it is.
John Boyden

---

### Post by Picklegnome on 2005-07-03
I have a similar problem to the thread topic. I burned 2 CDs, one of the iso, one of the unpacked files, because I was not sure which I needed. I've tried booting from each of them, and the same thing happens with both:
1. I insert the CD and reboot the computer
2. I hold the "C" key down
3. The computer boots up, but all I see is a black screen for about 30 seconds
4. While I'm still holding the "C" key, OS X boots up successfully.

I've tried it with both CDs, and the same thing happens with both.
Any ideas?

---

### Post by colinhayes on 2005-07-03
You don't want to do the same thing though,

when you initially boot into the cd, and it prompts you what to boot off of the cd, on your G4 you probably typed live-power3, well on a g5, you need live-power4, it won't work any other way.

bluetooth may also be a problem, I have no clue if the livecd has bluetooth support.

---

### Post by zenrick on 2005-07-04
[QUOTE=john boyden]I got by the white screen problem (Mac G5) by re-booting the live cd,
instead of typing "live" I typed "help" which gave me the option
of other things to type if I pressed tab.  I selected "live-power4"
and Ubuntu booted successfully.  I then encountered another
problem which I havn't been able to solve;  a screen came up which
wanted me so select a language, english was pre-selected but pressing
enter had no effect, the keyboard seemed to be absolutely dead.
If anyone has the solution I'd be glad to know what it is.
John Boyden[/QUOTE]
 John,

Something similar happened to me with another distro, can't remember which one. The keyboard would not respond, pressing enter did nothing, and I decided to try the space bar and that acted like the enter key. You might want to try this, if you haven't already.

BTW, is your Mac an iMac G5? My iMac G5 will not budge even if I type "live-power4". It goes beyond the white screen but at the next screen there's a kernel panic and then the fans start going full throttle so violently it sounds like a plane getting ready to take off...

Also, I'm using a wired Apple keyboard, but I have a Bluetooth mouse; not sure if that makes a difference...

---

### Post by kmi on 2005-07-05
The bluetoooth module (if it exists) can't be loaded before the prompt in my opinion... To type 'live-power4' or whatever, you certainly have to use a wired keyboard...

(Hope you understand my english !...)

---

### Post by M-Rick on 2005-07-18
I have been able to boot on my iMac, but I encountered another problem, my K04F pioneer drive is not supported by ubuntu ....

---

### Post by everettattebury on 2005-07-22
[QUOTE=john boyden]I got by the white screen problem (Mac G5) by re-booting the live cd,
instead of typing "live" I typed "help" which gave me the option
of other things to type if I pressed tab.  I selected "live-power4"
and Ubuntu booted successfully.  I then encountered another
problem which I havn't been able to solve;  a screen came up which
wanted me so select a language, english was pre-selected but pressing
enter had no effect, the keyboard seemed to be absolutely dead.
If anyone has the solution I'd be glad to know what it is.
John Boyden[/QUOTE]
 Try using the arrow keys to go down then back up before hitting enter, that worked for me.

---

### Post by MacUser on 2005-07-23
I'm having the exact same issue as zenrick.  My computer is an iMac 2GHz.  Any help appreciated.

---

### Post by MacUser on 2005-07-24
Just to reiterate for Ubuntu developers, the Hoary Live CD will not work in any second generation iMac G5 units.  Not only are their errors, but the fact that the software is somehow causing the cpu fan to run at abnormally high speeds is disturbing, the fan in the iMac has never spun that fast even at maximum cpu usage in Mac OS X Tiger.

---

### Post by M-Rick on 2005-07-24
They made support for G5 fans under YellowDog Linux, maybe it is possible to take the sources and integrate it in Ubuntu ?

 ... with new support for:
# Thermal (fan) for G5s Power Macs.
# Sleep for most ATI-based portables.
# iMac G5 (sans on-board audio, modem, thermal).
# Mac mini (sans on-board audio, modem).
# Updated ALSA sound driver for all non-G5 hardware.
# Griffin iMic USB audio device support.
# XMMS startup crash fixed.
# Security updates.
# Installer bug fixes.

---

### Post by avatar1349 on 2005-08-19
I booted a Live-CD ubuntu 5.10 which was first unsuccesfull (iMac G5 2nd generation/may 2005); then again using live-powerpc64 and all went well UNTIL
choosing the resolution. I did (safewise) 800x600 but then all froze solid; tried different resolutions but the same result.
the rev's of the fan went down to normal speed, so that works allright.
Anyone come accros the same problem??
Any info is welcome

---

### Post by M-Rick on 2005-08-19
[QUOTE=avatar1349]I booted a Live-CD ubuntu 5.10 which was first unsuccesfull (iMac G5 2nd generation/may 2005); then again using live-powerpc64 and all went well UNTIL
choosing the resolution. I did (safewise) 800x600 but then all froze solid; tried different resolutions but the same result.
the rev's of the fan went down to normal speed, so that works allright.
Anyone come accros the same problem??
Any info is welcome[/QUOTE]

Where did you get 5.10 ??? I only find 5.04

---

### Post by sgmorr on 2005-09-18
5.10 live is out as a preview release. It works fine on my flat panel iMac G4 1GHz.

---

### Post by M-Rick on 2005-09-18
Does it manage Firewire boot natively and thermal fans ?

I tried Suse 10 RC1 and provides all of this easily.
For the fan there is a patch to apply for the moment, but I think in the final it would be Ok.

And for the Firewire boot support, no problem, just partition the HD before because actually there is a bug in the installer, but when done everything is ok !

And the isntallation is as easy as Ubuntu, choice betwen KDE environment, Gnome or minimal.
There is also a possibility to choose manually the packages if desired.
The installation is in a graphical environment. Also it support PPC 64.

Uses all the latest packages, with Kernel 2.6.13, Kernel 2.6.13 ppc64, Gnome 2.12, Evolution 2.4, Nvu, Scribus 1.2, Gimp 2.2.8 + 2.3.3, OOo 2, KDE 3.4.2, Inkscape 1.42 (intalled by default when selecting Gnome) ...

---

### Post by avatar1349 on 2005-09-24
For distro's have a look at
[http://distrowatch.com](http://distrowatch.com)

Regarding Ubuntu on a iMac G5 (may 2005), with me it went al well UNTIL it should load x-windows, but all froze and kept it like that for 15 min, then turned it off.
Apparently it only seems to boot well on a mini-mac and/or powerpc and is the iMac somehow stuck in the corner.
If you boot Ubuntu boot it like live-powerpc64 (as a example).
Its a shame if it keeps being narrowed to older iMacs and/or 2nd gen PowerPC's, because a lot of users do have a iMac G5.
Hope this will improve in the future, otherwise I'll be forced to go back to my Sun Workstation

avatar1349

---


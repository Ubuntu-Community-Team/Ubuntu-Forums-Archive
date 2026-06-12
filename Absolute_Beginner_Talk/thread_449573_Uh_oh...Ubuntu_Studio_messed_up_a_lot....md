---
title: "Uh oh...Ubuntu Studio messed up a lot..."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by DeadSuperHero on 2007-05-20
Ok, so the other day, I decided to download the stuff for Ubuntu Studio out of Synaptic. Well, I accidentally downloaded all of it, and it thought I was upgrading. I restarted, and ended up in a mode with only a black screen and text. I finally managed to get in through the GRUB boot menu, but the other day, Beyrl stopped working, and every time I start up, I have to log out and log back in to make the GNOME bar show up.
So, I tried uninstalling this stuff through Synaptic, and it runs EVEN WORSE.
I have three options:
1. Reinstall all of the settings, and find whatever packages were missing. (But what are they?)
2. Uninstall the lowlatency mode, and whatever dependancies US had.
3. Do a fresh install, and back up my files.

So, what should I do? I've got lots of music, game, movie, and data files, and that would take a while to back up everything.
Do I have to do a fresh install to get everything working again?
Please help.

---

### Post by DeadSuperHero on 2007-05-20
Can someone please help me with this?
Should I just intall over, and slowly put my files back on there, or should I uninstall certain depandancies, or what?
I really want to have beryl working again, and none of this weird crap happening.

---

### Post by nalmeth on 2007-05-20
The reason you were getting the black screen was because your binary video driver doesn't work with the lowlatency kernel. By default you were booting into the lowlatency kernel (because the new kernel becomes the default kernel in GRUB), while running the non-free drivers. 

It sounds like you've figured out working with GRUB, but to be sure, when GRUB starts loading hit ESC to show the grub menu. Then pick the 2.6.20-15-generic kernel.

To turn on/off the binary driver (if you're using feisty), go into System - Administration - Restricted Drivers Management

To see what you installed with the ubuntustudio metapackages, open the terminal (Applications -> Accessories -> Terminal)
```
apt-cache search ubuntustudio

ubuntustudiolauncher - Music applications launcher
ubuntustudio-audio - Ubuntu Studio Audio Package
ubuntustudio-video - Ubuntu Studio video Package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package
ubuntustudio-desktop - Ubuntu Studio Desktop Package
ubuntustudio-graphics - Ubuntu Studio graphics Package
ubuntustudio-gdm-theme - Ubuntu Studio - GDM theme
ubuntustudio-icon-theme - UbuntuStudio Icon theme
ubuntustudio-look - Ubuntustudio look - metapackage
ubuntustudio-session-splashes - Ubuntu Studio look - Session splashes
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
ubuntustudio-default-settings - Default settings and artwork for the UbuntuStudio desktop
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-artwork - UbuntuStudio themes and artwork
ubuntustudio-screensaver - UbuntuStudio screensaver
```To see what was installed along with these metapackages, use this command:
```
apt-cache show ubuntustudio-audio

Package: ubuntustudio-audio
Priority: optional
Section: metapackages
Installed-Size: 32
Maintainer: Joseph Jackson IV <jjacksoniv@fluxbuntu.org>
Architecture: i386
Source: ubuntustudio-meta
Version: 0.2
Depends: aconnectgui, alsa-tools, alsa-tools-gui, ardour, audacity, beast, bitscope, bristol, creox, csound, denemo, fluidsynth, freebirth, freqtweak, gtick, hydrogen, jack-rack, jack-tools, jackbeat, jackd, jackeq, jamin, jdelay, lilypond, lilypond-data, meterbridge, mixxx, muse, patchage, puredata, qamix, qjackctl, qsynth, rosegarden4, seq24, shaketracker, sooperlooper, swami, tapiir, terminatorx, timemachine, timidity, tk707, vkeybd, wired, xmms, xmms-jackasyn, xmms-modplug, zynaddsubfx
Recommends: linux-image-lowlatency
Filename: dists/feisty/main/binary-i386/ubuntustudio-audio_0.2_i386.deb
Size: 2804
MD5sum: 8f40f341b5fc23b3ab959e3a9304d874
Description: Ubuntu Studio Audio Package
 Ubuntu Studio is a multimedia creation flavor of Ubuntu for the
 Linux audio, video, and graphic enthusiast or professional.
 .
 A collection of applications aimed at audio creation and editing.

Package: ubuntustudio-audio
Priority: optional
Section: universe/base
Installed-Size: 32
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Joseph Jackson IV <jjacksoniv@fluxbuntu.org>
Architecture: i386
Source: ubuntustudio-meta
Version: 0.1
Depends: aconnectgui, alsa-tools, alsa-tools-gui, ams, amsynth, ardour-gtk, ardour-session-exchange, audacity, beast, bitscope, bristol, cheesetracker, creox, csound, denemo, ecamegapedal, ecasound, fluidsynth, freebirth, freewheeling, freqtweak, galan, gmorgan, gnusound, gtick, horgand, hydrogen, jack-rack, jack-tools, jackbeat, jackd, jackeq, jamin, jdelay, kaconnect, kluppe, lilypond, lilypond-data, lmms, meterbridge, mixxx, muse, mx44, om, patchage, puredata, qamix, qarecord, qjackctl, qmidiarp, qmidicontrol, qmidiroute, qsampler, qsynth, rezound, rosegarden4, seq24, shaketracker, solfege, sooperlooper, soundstretch, soundtracker, specimen, spiralsynthmodular, supercollider, swami, sweep, tapiir, terminatorx, timemachine, timidity, tk707, vkeybd, xmms, xmms-jackasyn, xmms-modplug, zynaddsubfx
Filename: pool/universe/u/ubuntustudio-meta/ubuntustudio-audio_0.1_i386.deb
Size: 2144
MD5sum: 1968e1644c903fa1f4f69a5ac61f06ea
SHA1: 5e483b13435ac14b29a8b66c601545ae0c718d8e
SHA256: 165ee87f1d234be3496e4a073de51a62ee2e4944496035fb2c36380bec9df7ac
Description: Ubuntu Studio Audio Package
 Ubuntu Studio is a multimedia creation flavor of Ubuntu for the
 Linux audio, video, and graphic enthusiast or professional.
 .
 A collection of applications aimed at audio creation and editing.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```I would recommend uninstalling the linux-image-lowlatency kernel for now. 
**In the future when you are installing large metapackages, install them with the terminal, and with the aptitude command.**

```
sudo aptitude update
sudo aptitude install ubuntustudio-audio
```

This way, uninstalling all the packages that came with it is as easy as:
sudo aptitude remove ubuntustudio-audio

With Synaptic (which uses apt-get rather than aptitude), it is not this easy.
Hopefully this helped you out some

---

### Post by DeadSuperHero on 2007-05-20
Well, I removed the lowlatency stuff, thank God.
But there's still just two problems:

-Beyrl doesn't work anymore, but desktop effects do.
-The first time I login, the GNOME panel is missing. So, I have to push the power button, and the quit screen comes up. When I log out, then log back in, the Panel's there. How do I fix this?

Any advice would be great. But my main concern is getting Beyrl to work again, I could spend hours just messing with the screen and laughing like a four year old.

Anywho, thanks so far.

---

### Post by nalmeth on 2007-05-20
What method did you use to install Beryl? Redoing those steps may be a good way to fix it. 
Did you ever have to add any lines to /etc/X11/xorg.conf ?
Did you recently upgrade Beryl, or install a different version?

About the gnome-panel, I can't be sure what is causing that, but

When you log in hit Alt-F2 and run:
killall gnome-panel

It should come back. Or if you can't do this, do your log-out/in trick, go into System - Preferences - Sessions 
Go into Session Options and save the session when you DO have your panel, and maybe it will stick.

---

### Post by DeadSuperHero on 2007-05-20
I installed Beryl through the Add/Remove Programs tool.
It worked fine without any configurations at all...until I made the Ubuntu Studio mistake. (Nothing against it, just didn't do it right anyway)

Perhaps I should open the xorg file...hmmm...
Here's the thing, though: desktop effects work. So I dunno.

---


---
title: "g4 cube hardy liveCD w/ 15&quot; Studio Display and ATI Rage 128 - steps to boot"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by digidoodle on 2008-05-11
Hi - I spent a bunch of time to get my stock g4 cube with 15" studio display and ATI Rage 128 Pro video card running Ubuntu 8.04. So ... here are the steps I took to get the standard LiveCD (ubuntu-8.04-desktop-powerpc.iso) up and running. Perhaps this will be helpful to somebody else.

Boot the computer holding down the "c" key with the Ubuntu LiveCD in the drive. At the boot prompt, type:

live-nosplash-powerpc video=r128

Wait awhile ... eventually you will have a black screen after the gnome display manager tries to load. Type ctrl-option-f1 to get to a prompt, then type:

sudo killall gdm

This will stop gnome from loading. Next we need to edit the xorg.conf file. This thread - [http://ubuntuforums.org/showthread.php?t=772808](http://ubuntuforums.org/showthread.php?t=772808) - had the settings that work for me. Using nano or your favorite text editor, do the following:

sudo nano /etc/X11/xorg.conf

In the Monitor section you'll need to add the Horizsync and Vertrefresh:

Section "Monitor"
Identifier "Configured Monitor"
Horizsync 28-51
Vertrefresh 43-60
EndSection

In the Screen section add a Display subsection:

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Modes "1024x768"
EndSubSection
EndSection

At the end of the file, add the following:

Section "DRI"
Mode 0666
EndSection

Save your changes and exit (ctrl-x in nano). Type:

sudo /etc/init.d/gdm start

If all goes well, gnome loads and you are on your way. I did an install to the G4 Cube hard drive, which went well. After rebooting, everything loaded up just fine with no user intervention (cheer). Trying to do updates, the updater crashed once, but after rebooting, I was able to finish all updates. I set this up hoping I could get MythTV backend up and running, but seems like many myth components do not yet have ppc packages. Oh well...

A couple things to note:

Sound might not be working ... I don't have speakers plugged in but my volume control has an "X" through it.

The standard airport card does not support WPA in Ubuntu - there may be a workaround but none of them appear to be very simple - I'm just plugged in via ethernet for now.

---

### Post by stream303 on 2008-05-11
> **digidoodle said:**
> Sound might not be working ... I don't have speakers plugged in but my volume control has an "X" through it.

Nice - thanks for sharing.  You're the second Cube-owner I've run into here.

For me, I can't trust the gui volume-applet and volume control at this time; the only reliable thing for me is to run alsamixer in a terminal.  The gui applet may show that the master is muted, when in fact it is not, or visca versca.  It doesn't seem to depend on whether I use alsa or pulseaudio or not.

Assuming there aren't other problems, try using alsamixer to toggle mute (m key), balance (b key) levels, etc.  The gui may not report the status accurately, but you won't know until you hook up some speakers. :)

Anyway, congrats on the Cube!

---


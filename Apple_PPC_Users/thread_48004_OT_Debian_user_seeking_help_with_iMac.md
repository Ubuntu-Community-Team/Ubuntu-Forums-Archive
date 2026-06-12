---
title: "OT: Debian user seeking help with iMac"
date: 2005-07-10
forum: Apple PPC Users
---

### Post by bedouin on 2005-07-10
Yes I know this is for Ubuntu support, but I figured I would ask because the community seems friendly.  Oddly enough, when Googling for Debian PPC questions I often end up in the Ubuntu forums.  Solutions that work for Ubuntu often work for Debian as well, so maybe someone can help me out :)

I've been using Sarge on my iMac Dv 400 for about a month now, with mostly positive results.  However there are two issues bothering me that I haven't been able to resolve, and nobody on the Debian lists has been able to answer for me either.

First, as many of you might know, the iMac DV has four different audio outputs: the built-in speakers, the two headphone jacks on the front, and the line-out jack on the side.  The problem I'm encountering is that Linux is assigning the line out jack as the master volume control, and the built-in speakers as "PC speaker."  This isn't a big deal, but it makes controlling the volume via keyboard shortcuts, or from mixer applets difficult (they all default to the master volume control, with no ability to modify that).  Is there some way I could have the built-in speakers become my master output?

Secondly, this is the first iMac I've ever owned, so I'm unaware of how these machines typically handled power management.  More specifically, I heard a rumor that the CRT iMac displays could not go into deep sleep (i.e. standby mode) because the heat they generate is part of the machine's cooling convention.  The display seems to do more than just blank, since I cannot see the slight glow of a blanked display when the lights are turned off.  However, when moving the mouse the display wakes up instantly; is the mechanism for sleeping a CRT iMac's display somewhat different than other machines?

Thanks in advance!

---

### Post by pvz on 2005-07-11
I'm having the same issues on my iMac DV 600.. It runs Kububtu just fine, but power management doesn't seem to be complete. The monitor goes dark, but the system doesn't go into hybernation. It used to work just fine on my 233 mhhz first generation CRT iMac, both Kubuntu and Debian sarge. But that machine had a cooling fan, while the newer ones don't, maybe it is indeed some sort of cooling issue.
Sound works alright here, using alsa and KDE, I can change the volumes of built-in speakers and lineout jack. But It took me some messing around with alsa and kmix to establish that.
I am curious about this power management issue though. I would like to have full hybernation so I don't have to switch off the computer anymore.

---

### Post by brim4brim on 2005-07-11
[QUOTE=bedouin] This isn't a big deal, but it makes controlling the volume via keyboard shortcuts, or from mixer applets difficult (they all default to the master volume control, with no ability to modify that).  [/QUOTE]

In Gnome (all I have real experience with, all my experiences with KDE have been bad) if you select the properties of the speaker icon you can select which bar to modify.  Now that won't let you modify the input it takes from your device but it may/should give you an easier way to control the volume of the device.

You can change it to anything with Gnome including microphone and digital and phone in's etc...

Maybe that might give you easier control over the volume if you can select the one you want to icon to control.

---

### Post by bedouin on 2005-07-11
[QUOTE=brim4brim]In Gnome (all I have real experience with, all my experiences with KDE have been bad) if you select the properties of the speaker icon you can select which bar to modify.  Now that won't let you modify the input it takes from your device but it may/should give you an easier way to control the volume of the device.

You can change it to anything with Gnome including microphone and digital and phone in's etc...

Maybe that might give you easier control over the volume if you can select the one you want to icon to control.[/QUOTE]

Unfortunately there's an applet I find indispensable that has no equivalent in GNOME, so I'm stuck in KDE for the time being.  KDE's mixer applet doesn't let you assign a specific channel to the master slider.

---

### Post by stereo on 2005-07-13
sleep-mode is different with different kernels.
in 2.6.8 (i guess) she goes into deep-sleep (suspend to ram).harddisk off.

2.6.10+ only screen-blank

but with the same hal-deamon problem as an ibook. 


i've got an imac blueberry 350mhz. i have a problem with the  external speakers. they are completely overdriven. anyone the same problem?

---

### Post by bedouin on 2005-07-13
[QUOTE=stereo]i've got an imac blueberry 350mhz. i have a problem with the  external speakers. they are completely overdriven. anyone the same problem?[/QUOTE]

Yeah, that's another issue.  If you plug headphones into the line-out jack and move the volume level any higher than say, 35%, the sound distorts horribly. 

There's another issue I'm having that I've requested help with on the KDE mailing list, but left it out here since Ubuntu uses GNOME.

I prefer to use Macintosh keyboard modifiers in KDE, and have KDE configured to do so.  However, if you're using more than one language and switch between them using KDE's keyboard switcher, it overrides the Macintosh key modifiers and sets them back to Windows -- probably because KDE has no Mac keyboard maps.

---


---
title: "Volume Control in Dapper on iMac G3"
date: 2006-06-21
forum: Apple PPC Users
---

### Post by daft_ska on 2006-06-21
Two very strange things keep happening to my volume controls after installing Ubuntu Dapper.

(Let me preface this by saying I do hear a sound every time I'm supposed to in any app I've used so far)

1. Volume control doesn't control volume.  For the life of me I have not been able to figure out why the any volume setting I keep changing does not affect the volume.  This is most noticable while using gaim, as sometimes those effects are just a bit too loud where they are currently set.  I've tried all sorts of mixer installations using synaptic, alsa-mixer, I tried installing the xfce desktop even, to see if xfce could control the volume, but it too cannot, and it is also experiencing the same problem as gnome, with:

2. The mac volume keys call the volume functions, down, up and mute.  Every key looks like it's supposed to be doing it's job, as in mute graphically shows the volume being muted, down moves the meter down, up makes the volume window pop up, but the bar does not go up! It doesn't go down, it doesn't mute.  The status window just pops up and refuses to move up.  This really isn't too big an issue as I can't even control the real volume with the meter anyway, but I digress.

If I remeber right, Breezy didn't have any of these problems.

Anyone else ran into this problem?

---

### Post by psignosis on 2006-06-21
Yes, I have the same problem here.  I don't know if this occurred in Breezy as I immediately upgraded to Dapper without investigating Breezy first, following the disabling (first) of DRI in xorg.conf to even get the install to work.

---

### Post by linear on 2006-06-21
There are some issues with alsa support on PPC soundcards ([http://wiki.debian.org/?PowerpcSoundcards]("http://wiki.debian.org/?PowerpcSoundcards")), but they existed in Breezy as well.

---

### Post by avtolle on 2006-06-21
Does clicking on the speaker symbol at (in my case) the top panel bring up a slider for volume control, and if so, can you move it up and down with your mouse? If this is working, with no change in volume, then someone else will need to assist, for I'm as new to this as you.

---

### Post by daft_ska on 2006-06-22
Yeah, I can move that, but no, no difference.  I tried running alsamixer from the console and that, too had no effect.  I believe this is the "screamer" sound card, and it was indeed listed as working on that page.  Is there some way to perhaps re-install all drivers, oss, alsa, and (SDL?) and see if that's an issue? It seems to be that perhaps something else is in control of sound volume, and isn't letting the alsa mixer do it's thing.

---

### Post by daft_ska on 2006-06-29
Update:
Okay, I have found that my iMac can be controlled by setting the panel volume control to PC Speaker, not Master.  But, this still doesn't change the fact that keyboard shortcuts (from the System -> Preferences) aren't mapped to PC Speaker, perhaps they are routed to something else.  How do I reroute the Keyboard Shortcuts to point to PC Speaker and not whatever it is pointing to?

---

### Post by SuperSlug on 2006-06-29
I've been looking and asking for an answer to this problem for weeks.  There does not appear to be a way of changing which volume control the default desktop volume control sets.

Sigh...

SuperSlug

---

### Post by digs on 2006-06-29
See if "modprobe snd_mixer_oss" triggers the mixer.

---

### Post by daft_ska on 2006-06-30
"modprobe snd_mixer_oss" doesn't do anything outright, in that no new window pops up, and I just get back another command prompt.  I have noticed that I'm able to control the volume of Sound Juicer playing a CD with the panel being set to both ALSA's PC Speaker and OSS's Volume settings.  However, the keyboard shortcuts still bring up a mac-like volume icon with a meter, but only down and mute work, and they have no control over volume.  Any more thoughts?

---

### Post by mehmehmeh on 2006-07-17
I'm not sure if this is the same problem i'm running xubuntu on a imac dv se 400. My keyboard is the original imac keyboard (smaller, came with puck mouse) So i cann't figure out how to control the volume at all from keyboard. when i got to system settings > sound pannel, there is a only a drop down at the top of the pannel that has the options for default or powerpc screamer i think. below that are just check boxes next to the vairous inputs outputs for the computer. I don't see volume sliders anywhere.

---

### Post by mehmehmeh on 2006-07-17
never mind, i got volume control by right clicking (or F12 since i still have the hock puck mouse) on the task bar at the bottom of the screen and adding a volume control icon to the task bar.

---


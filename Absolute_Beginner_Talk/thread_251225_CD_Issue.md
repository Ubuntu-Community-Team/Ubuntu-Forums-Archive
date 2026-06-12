---
title: "CD Issue"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by kockbeard on 2006-09-05
Cheers for the help yesterday you guys managed to get me through my first partition with no problem and feeling confident, however I keep discovering more things that confuse me, which is good cause it means I'll get competent sooner rather than later. I'm currently adding my music collection, however some of my CD's (not only ones with anti-copy, but also ones with WMA videos and things as extras) won't extract through Sound Juicer.

My questions are, is Sound Juicer a very underpowered tool, that I should use a different program?? Or am I just doing something wrong, is there a way to get the videos off the CD's and into a jukebox as well?? At some point I'll have to take the computer to the lounge to record my Vinyl anyway, so I could use my preamp and XLR jacks on the sound card to record them straight from my CD Source, but this means even longer with the house all round the wrong way. Also can you recommend a recording program to get my vinyl onto the machine.

---

### Post by monktbd on 2006-09-05
i use grip for ripping and encoding.
for the wma files: you should be able to just copy them in nautilus. i might be wrong though.

for recording your vinyl collection my choice would be audacity.

---

### Post by xyz on 2006-09-05
Take a minute too read the following (it's short); it states precisely what DVD ripper does; that way you'll be able to tell if it is indeed what you need:
[http://www.exit1.org/dvdrip/features.cipp](http://www.exit1.org/dvdrip/features.cipp)
I think DVD ripper's also in Automatix if this can make easier on you.

You can "do" vynils but I'll have to check further on that.

---

### Post by xyz on 2006-09-05
**rickh** on linuxquestions.org says about vynils:
> Audacity ... to rip to .wav
gwc ... to clean vinyl noise
lame ... for mass conversions to .mp3

I checked...they can all be downloaded from Synaptic. Let us know how it goes! Good luck.

---

### Post by kockbeard on 2006-09-06
These aren't CDs that I've burnt but some music discs you buy call themselves as "enhanced cds" I guess that the .exe files on them are playing silly buggers with Sound Juicer, I'm about to try Grip, I don't yet have a DVD drive so I'll wait a while before trying DVDRipper, cheers guys will update later.

---

### Post by xyz on 2006-09-06
OK, kockbeard, I understand what you mean! However, I don't know what "enhanced cds" are. When you have a minute to spare, I'd appreciate a short explanation. Thanks.

---

### Post by steve.horsley on 2006-09-06
My guess is that they are "enhanced" with DRM - encrypted so that they can only be played by the .exe files that install a windows root kit and prevent you from copying the music to your ipod.

---

### Post by kockbeard on 2006-09-06
I listen to a lot of "samplers" a CD pressed by a label that includes one or two songs from all the bands on the label and some unreleased or alternative versions of tracks, so hopefully you hear a band you'd not heard before then go and buy more music from the label.

When you play these CD's in a CD Player they play as a normal CD would, however in a Windows machine they normally open a flash window and include "extras" like music videos or weblinks to videos, band sites etc, whereby the site challenges the browser and the key is on the cd so these sites are exclusive to the CD owners.

Now I'm not too fussed about the videos and stuff though if you know how to copy them from the CD and put them into Amarok that'd be great, but in iTunes these CD's play and encode straight away, however SoundJuicer doesn't do anything with them and in fact the CD-RW drive shows as empty when one of these discs is in it.

---

### Post by kockbeard on 2006-09-06
Sorry to bump, but seeing as how Ubuntu lends itself to being a home media server so well I figure this could help others as well

---

### Post by xyz on 2006-09-06
> if you know how to copy them from the CD and put them into Amarok
I'm not familiar enough with Amarok but I've taken a very quick look at the Amarok Forum! Perhaps you could dig in there a bit or ask pro Amarok users?
[http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)

Not sure whether this *totally* is relevent to your case:
> **Tags**. amaroK is a collection-driven player. Most popular video containers (avi, mpeg, wmv) do not support tags such as \"Artist\" or \"Title\", so the videos couldn\'t be added to the collection.

**Unix-way**. It says: use one app for one set of (related) tasks. Playing audio and video are different tasks, and require different apps.

**Work**. Adding video support will require more work than it seems. Yeah, xine and gstreamer can both play video fine. But adding video support to amaroK would require much work. Even the redesign of the UI would take weeks. Moreover, video player requires functions that an audioplayer doesn\'t need (for example, gamma correction or changing A/V offset). Coding these will take time and skill (maybe it will require to join efforts with the devs of some video player). In the end there will likely be an audio player with some very rudimentary video support, with much more bugs (each new feature almost always adds bugs, so that\'s why not all feature requests are welcomed by the devs) and a longer release cycle.

From what I understand, video-related stuff seems to cause pbms in Amarok. If you care to visit their forum more 'in depth' than I did, let me know what you find out!
:-k

---


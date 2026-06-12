---
title: "Somewhere, someone must be watching Kill Bill on ubuntu."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by slikwill on 2007-10-15
There is no plug-in to handle this movie
This is what I get after following the HOWTO for Multimedia given in the sticky part of this forum.  Also installed Movie Player Totem.  Just trying to play my "Kill Bill Vol. 1", so I just need a plugin name, not another Multimedia installation tutorial.

---

### Post by 3rdalbum on 2007-10-15
Try installing VLC movie player - it's much better as a DVD player. I never managed to get Totem working for DVDs anyway :-(

---

### Post by wheredidrealitygo on 2007-10-15
libdvdcss2 is the name of the package

enable medibuntu repository (google medibuntu), update your apt-get (or update synaptic) install libdvdcss2 and dvd playback should work after that.

i recommend vlc for video :)

---

### Post by tact on 2007-10-15
It would help to know what format the movie is in?  Its just a commercially bought DVD movie is it?  Or something you downloaded?   You got any info on this?

When you put the DVD in your drive I presume that you get an icon on your desktop (as well as a movie player popping up but apparently failing to play the movie?).

If so can you right click and open the DVD folder and see any files in there (e.g. video_ts directory and a bunch of VOB files inside etc?)

The more help you are the more help you get.

For what its worth commercially bought and downloaded DVD's play find for me using either VLC or the default movie player.  I installed the "ubuntu-restricted-extras" package via synaptic and basically nothing else.

---

### Post by slikwill on 2007-10-16
Yes!  VLC did the trick.  This is just a commercial DVD.
Anyway, how do I make VLC the default player instead of totem?

Thanks again.

---

### Post by Dr Small on 2007-10-16
Right Click on a file > Properties > Open With (and change what that filetype opens with, there.)

Dr Small

---

### Post by asmoore82 on 2007-10-16
> **slikwill said:**
> Yes!  VLC did the trick.  This is just a commercial DVD.
Anyway, how do I make VLC the default player instead of totem?

Thanks again.

open "System -> Preferences -> Removable Drives and Storage"
go to the "Multimedia" (2nd) tab
check command at "play video DVD when instered ..."

---

### Post by bliffle on 2007-10-16
Another win for VLC!

---

### Post by hyper_ch on 2007-10-16
vlc was also my default video player back on Windoze... it just works on almost any media format.

---

### Post by GepettoBR on 2007-10-16
VLC is much more buggy in Windows, though. Either way, I use mPlayer. My hardware isn't that good and since the player is really light it manages to decode higher-bitrate files without significant framedrops or skipping. It also has internal decoders - in fact, VLC uses the mPlayer library.

---

### Post by hyper_ch on 2007-10-16
it may be more buggy on windoze but it's still the best media player out there in the windoze world.

---

### Post by GepettoBR on 2007-10-16
> **hyper_ch said:**
> it may be more buggy on windoze but it's still the best media player out there in the windoze world.

I completely disagree. It's just easier to use because there is no need to install codecs, but the internal decoders (especially for newer compression technologies, like H.264/MPEG-4 AVC and the experimental codec SNOW) are very inferior to what you can get by properly empowering Windows to decode the appropriate FourCC. mPlayer also suffers from this problem. It's best to use wide-range decoders like ffdshow and safe splitters like Haali's (both FOSS and contained in the [Combined Community Codec Pack](http://www.cccp-project.net/)) that will allow you to view your videos in any media player than to rely on standalone platforms, especially because when you encounter a problem they're more likely to provide a fix quickly. My excuse for mPlayer is that it's light, but if my current hardware allowed it, I'd use FFDshow via Media Player Classic (which I do for all my non-HD/low bitrate content).

People tend to prefer VLC and mPlayer because they get confused with all the different codec packs out there (and CCCP is the only one worth anything -  the fact that most of them are crap does not help) so they're overjoyed to find something that saves them the hassle. And as far as functionality goes, VLC suffers a lot: It's support for A.S.S (Advanced Substation Alpha - ignore the weird dots, the word filter thinks I'm swearing :)) subtitles is broken, it does an awful job resizing if you want to change the aspect ratio on the fly and the seeking is actually less accurate than with directshow decoders.

---

### Post by hyper_ch on 2007-10-16
Depends on the metrics you apply to define "best" ;)

---

### Post by slikwill on 2007-10-16
The System->Preference did the trick.  Thanks asmoore82.

---

### Post by GepettoBR on 2007-10-16
> **hyper_ch said:**
> Depends on the metrics you apply to define "best" ;)


Of course :) I was just giving my input.

---


---
title: "No Sound when playing DVD"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-04-07
Hi all, 

I've been trying to get DVDs to play in Totem media player.  I've been through the forums.  First I downloaded and installed the codecs, I've downloaded and installed the various libraries from the restricted formats and mediabuntu pages.  I fixed the missing plugin problem.   I actually have the video running now, but get no sound.  I've adjusted the alsa mixer to the max for everything.  Not sure what to do next.  Any suggestions would be appreciated.  

Thanks.

---

### Post by oilchangeguy on 2007-04-07
do you have sound for everything else? did you make sure the mixer is not set to mute?

---

### Post by nudnik on 2007-04-07
> **thefoolisme said:**
> Hi all, 

I've been trying to get DVDs to play in Totem media player.  I've been through the forums.  First I downloaded and installed the codecs, I've downloaded and installed the various libraries from the restricted formats and mediabuntu pages.  I fixed the missing plugin problem.   I actually have the video running now, but get no sound.  I've adjusted the alsa mixer to the max for everything.  Not sure what to do next.  Any suggestions would be appreciated.  

Thanks.

This might be an annoying question, feel free to beat me senseless if it is. Is the volume turned all the way up on the player itself? Have you tried other players such as VLC or Gxine? Is the version you have "totem-xine"?

---

### Post by mikeyphi on 2007-04-07
> **thefoolisme said:**
> Hi all, 

I've been trying to get DVDs to play in Totem media player.  I've been through the forums.  First I downloaded and installed the codecs, I've downloaded and installed the various libraries from the restricted formats and mediabuntu pages.  I fixed the missing plugin problem.   I actually have the video running now, but get no sound.  I've adjusted the alsa mixer to the max for everything.  Not sure what to do next.  Any suggestions would be appreciated.  

Thanks.

When you've tried everything else - go here - [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by thefoolisme on 2007-04-07
Never mind folks, it was an I-D-1-0-T problem.  Yes, all the volumes everywhere were turned up to the max.  What I forgot, since I don't use this PC all the time is that there were two sound cards - one on the motherboard, and a PCI card installed.  I thought the motherboard card had been turned off in bios, but apparently not.  When I installed Ubuntu this morning, that was the sound card it installed.  I went through all the forum posts, and what I should have done was move the plug from one sound card to the other.  I'm truly a fool!

---

### Post by houstonbofh on 2007-04-07
After much fighting, I now use Ogle for DVD.  In synaptic, look for ogle-mmx and ogl-gui.

---


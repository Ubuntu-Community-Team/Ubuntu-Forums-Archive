---
title: "How do I get .wmv's to play?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-09-04
I thought the codec was available from Automatix but it still doesn't want to play.

---

### Post by manojvekaria on 2006-09-04
Have you tried amarok.

its a wonderful piece of software. replacement of real jukebox, media player, and winamp.

try the code:

sudo aptitude update
sudo aptitude amarok

You know how to install software's don't you. Or the the easier way is to use synaptic manager to get Amarok.

hope this helps you. mp3 wma and other many extensions are supported

---

### Post by Amablue on 2006-09-04
I already use amaroK for my music (most of it is .ogg anyway, but I do have a few mp3's). I didn't realize it could play videos though. I just tried it and just the sound came out, there was not picture. How do I get the video to play?

---

### Post by diggity on 2006-09-04
I had to uninstall Totem (it uses gstreamer by default) and install totem-xine.
After that I used [these instructions]("http://stanton-finley.net/fedora_core_5_installation_notes.html#Codecs") (there're for fedora, but work for ubuntu as well)
Just use sudo before the commands since Ubuntu doesn't use su

---

### Post by Amablue on 2006-09-04
amaroK is already using xine, and I followed those steps exactly and it's still not playing videos. I can hear the audio, but no picture shows up.

---

### Post by diggity on 2006-09-04
Is it all wmv files or only certain ones? I ask because there are different versions of wmv. I don't believe WMV 10 is supported in Linux as of yet.

---

### Post by xyz on 2006-09-04
Automatiy allows me to play .wmv! Did you check the mplayer firefox plugin in Automatix?

---

### Post by TheRingmaster on 2006-09-04
make sure you have w32codecs installed.

---

### Post by gkiller on 2006-09-04
You should follow these instructions, to install all the available codecs for Ubuntu (including w32codecs) and install mplayer:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

Then try to play the movie with mplayer. If that does not work then I would say you can forget it.

You could also try other media players: gxine or VLC (both available from Synaptic). There is no harm having them installed together. But mplayer is generally the best for WMV files. It supports up to Windows Media Video 9 (also called WMV3), but not WMV-HD or VC-1 (WVC1), which are all called WMV by Microsoft.

I don't know what Automatix installs because I don't use it (I prefer doing things myself and knowing what I'm doing ;)), but there is no harm installing them again manually (if it's already installed it simply does nothing).

---


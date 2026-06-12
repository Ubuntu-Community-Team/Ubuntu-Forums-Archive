---
title: "badly distorted sound for wav files"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by ukemike on 2008-03-30
We've been having troubles playing .wav files on my son's computer.  Most sound functions work well enough, but when we play .wav files they are very distorted.  I tried adjusting the settings using alsamixer as per this post:

[http://ubuntuforums.org/showthread.php?t=729711&highlight=distorted+sound](http://ubuntuforums.org/showthread.php?t=729711&highlight=distorted+sound)

But that didn't help.  Though I did get our volume for watching DVDs up to a more useful level.  When I open a wav file it plays in Totem, and I put it on repeat play so I could continue to hear the file play while adjusting the levels.  I noticed that every time the wav started again in alsamixer the level on PCM Font went up to max again!  Odd.  Anyway adjusting any of the sliders did nothing but change the volume, the distortion remained.

This is what the Kinfocenter says about my sound hardware

Sound Driver: 3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux blue 2.6.20-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686
Config options: 0

Installed Drivers:
Type 10 ALSA emulation

Card Config:
SiS Sl7018 PCI Audio at 0xdc00, irq 10

Audio devices:
0: Trident 4DWave (DUPLEX)

...

---

### Post by annda on 2008-03-30
just an idea: do you have the same problem while using other programs for playback? VLC and audacious?

---

### Post by kyphi on 2008-03-30
Each sound reproducing application has its own volume control as well as the main volume control on the panel of your desktop.  Possibly your Totem volume control is set too high.

You might consider using another application for playing your sound files (Totem is for visual media).

To use Rhythmbox, for example, right click on a .wav file and select properties from the dropdown menu.  Then go to "open with" and either select another programme or add it to the list and tick it (pressing "add" will result in a dropdown listing of your installed applications).

---

### Post by ukemike on 2008-03-30
I wondered why .wav s opened in totem.  We don't even use that for movies (caffeine seems more able to handle commercial DVDs).  I re-associated wavs with amorak and it works just fine.  Thanks.

---

### Post by ukemike on 2008-03-30
oddly though when downloading a wav from online then clicking open from the FF download window, it still uses totem.  I thought that would be easy to change, but I'm still struggling with it.

On my XP machine FF has about 33 file associations listed in the Tools-Options-Content-Filetypes menu, and it includes all of the obvious ones.  On our kubuntu machine it only has associations listed for two shockwave type files and oggs.  There are no associations for mp3s wavs mpg, etc.  It is obvious how to change these but not obvious how to add one...

---

### Post by mgmiller on 2008-03-30
Try installing the Firefox extension called MediaPlayerConnectivity.  It will allow you to select any installed player for any kind of media you run across.

---

### Post by ukemike on 2008-03-30
> **mgmiller said:**
> Try installing the Firefox extension called MediaPlayerConnectivity.  It will allow you to select any installed player for any kind of media you run across.

I've read that suggestion in a few spots.  I just tried it.  It only found kaffiene and totem.  So I manually pointed it to /usr/bin/amarok for the various sound a playlist types.  It still runs totem when I click on a wav.  I'm considering uninstalling totem.  I never use it by choice.


More background here.  The computer in question is my 4 year old son's computer.  I've got (mostly) everything on it set up to be really easy.  Icons with links to his favorite websites, autoplay on the DVDs, etc.  He is obsessed with Doctor Who, and would really love to be able to play sounds from this site:

[www.dwwa.net](www.dwwa.net)

it's the Doctor Who Wave Archive.  It has hundreds of audio captures from the show.  When you click on one it opens the download window, and then launches totem.

---

### Post by mgmiller on 2008-03-30
I have wav files set to /usr/bin/vlc in MediaPlayerConnectivity and I tried going to your Dr. who site and vlc pops up and plays the sound.  

Try installing vlc and then set the preferences in MediaPlayerConnectivity as above.

---


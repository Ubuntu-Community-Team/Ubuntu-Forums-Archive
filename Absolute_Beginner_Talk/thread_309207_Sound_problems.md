---
title: "Sound problems"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by izua on 2006-11-29
So, I got my taste in linux. I can use torrents, realised in mounting my windows partitions, and now comes the big issue.

I can't play any mp3. Amarok just skips through the playlists. XMMS, in a weird way, opened up just one song from Agathodaimon (umm, could it be that they're the first in the playlist, lol:p ). I changed the volume in XMMS and it stopped outputting (but still decoding, spectrum still poppin, progress bar moving). Changed the volume back, nothing happened. What's wrong?

Another issue in my transfer from win to kubuntu is that i'll need some sampler/tracker which supports VST. I'll also need to do some real-time processing, recording and monitoring for it (i'm an amateur guitar player).

Any ideas what should i look for?

---

### Post by taurus on 2006-11-29
Did you install the codecs for mp3s and videos/movies?

---

### Post by deadgobby on 2006-11-29
here is a link to Ubie Studio. All the cool stuff for your own little recording studio. If you have a good sound card like Sound Blaster. Your off recording. Most of Ubie Studio programs can be found in Synaptic
Gobby

[https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio)

---

### Post by izua on 2006-11-29
um..
I looked (yesterday) for codecs in synaptic, and marked for installation (and did installed) everything that looked important to me. I pwned my box really hard, kaffeine not working, ktorrent not working, if i started konqueror from terminal, it wasn't even thumbnailing stuff and errors were drifting on the terminal.

had to go back through the desinstallation process, and tried to remember each codec, untill everything was back to normal.I really don't know what/where are the codecs :)

---

### Post by taurus on 2006-11-29
Use automatix2, [http://www.getautomatix.com](http://www.getautomatix.com), to install the codecs and other goodies for your machine...

---

### Post by redDEADresolve on 2006-11-29
use easyubuntu or automatix for installing your codecs. 

I use automatix
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by izua on 2006-11-29
got automatix, installed codecs.

well, now it works. at least, theoretically, since the spectrum analyser in amarok pops, and it even highlights a song, but i can't hear a thing, and my amp is cranked up at max. 

i tried even the little speaker-driver icon, near the clock (like in win, hehe :) ) but everything is up, and i still don't hear anything.

---

### Post by taurus on 2006-11-29
Check your master sound controls/volumes with

```
alsamixer
```

---

### Post by izua on 2006-11-29
everything is up at 100.
uh.. well.

i have changed the engine in amarok, it crashed, and now it doesn't pop up the analyser anymore, it just says void engine can't play.

what have i done? :-s

later edit: ok, i fixed it. but i still can't hear anything. i did install audacity, and i don't see any devices in it's configuration for sound I/O.

---

### Post by izua on 2006-11-30
well, i edited and it's still on the second page.. :/
up you go!

now, i don't want to be a trouble maker, but it's hard, really hard, and ubuntu may not be the thing i need. i tried to get 3d desktop to run, and that didn't had even running instruction. ok, maybe, not even win 32 programs have, but i had to install a ton of stuff for 3ddesktop to work, which, of course, i wasn't able to.

All I'm trying, for 5 days is to find a way to listen to music and apply processing to my guitar. Is it something so hard, or what? :/

---

### Post by deadgobby on 2006-11-30
There is a program called Audacity for wave file recorder and editor. You can check how to use Audacity at the web site.
[http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
 There is Rezound a other sound recorder with some effects on it. 
There is a live CD for music studio called Musix, If you look at the software listing. All and most can be found in Synaptic. 
[http://www.musix.org.ar/en/index.html](http://www.musix.org.ar/en/index.html)
 No as for your sound. Do you have a sound card. If so, you may need to go into your BIOS and disable the on board sound device. You may need to install ALSA mixer. I do not use Kubie, but I think after the install. Open up your Terminal and type in alsamixer . This will bring up the ASLA  mixer and then you can push up the sound. 

Gobby

---

### Post by izua on 2006-11-30
yes, but i need something that delivers more performance then audacity.
think an alternative to cubase, nuendo or even fruity loops.

um, no, i don't have a sound card. i have only the one onboard.
everything is up in the alsa mixer, both output and monitoring.

---

### Post by sailor2001 on 2006-11-30
a simple question or two....are you using a desktop? If so, are the speakers plugged in front or Back? Is your alsa settings for the front ports or the back?

---


---
title: "can't play m4a sons :("
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by littleasian on 2007-11-07
hey guys

i recently got my music to work so im totally stoked.  however, i can't play m4a songs (aac format).  i've tried installing all the codecs in synaptic but im missing something.

can someone tell me which ones to install so i can play these songs??

---

### Post by TeaSwigger on 2007-11-07
Hello, do you have Medibuntu's repositories available?
[http://www.medibuntu.org/](http://www.medibuntu.org/)
Hopefully someone can tell you which to install as I can't remember which it was!

---

### Post by crazysexycool on 2007-11-07
Hi i use vlc player and it works wonderfully plays everything

---

### Post by littleasian on 2007-11-07
it says i need a gstreamer codec for playing the songs

but i already downloaded all of the codecs for playing mp3's and such, and it was included (acc format).

so im really confused why its not work...

btw im using exaile..could that be a problem?

---

### Post by justsomedude on 2007-11-07
Did you install the codecs Exaile (or whatever player you tried to open these files) suggested?

Also, is it possible these files were bought from the iTunes Music Store?

m4a is a container format btw, or to be more precise it's mp4. Apple uses the extension .m4a for mp4 containers containing aac. So, it could mean you've got the codecs for aac but the player cannot handle the container.

---

### Post by santiagoward2000 on 2007-11-07
> **littleasian said:**
> it says i need a gstreamer codec for playing the songs

but i already downloaded all of the codecs for playing mp3's and such, and it was included (acc format).

so im really confused why its not work...

btw im using exaile..could that be a problem?

I'm using Exaile and have no problem with the m4a files. Have you installed all the gstreamer packages form Add/Remove?

---

### Post by littleasian on 2007-11-07
are you talking about all of the gstreamer codecs in synaptic?

i installed the ones that that ubuntu prompted me to install.

there are like 30+ packages..should i install all of them?

---

### Post by santiagoward2000 on 2007-11-07
> **littleasian said:**
> are you talking about all of the gstreamer codecs in synaptic?

i installed the ones that that ubuntu prompted me to install.

there are like 30+ packages..should i install all of them?

I'll tell you those I have, but I'm not sure which one is for m4a files.
[LIST]
[*]gstreamer0.10-alsa
[*]gstreamer0.10-ffmpeg
[*]gstreamer0.10-fluendo-mpegdemux
[*]gstreamer0.10-gl
[*]gstreamer0.10-gnomevfs
[*]gstreamer0.10-pitfdll
[*]gstreamer0.10-plugins-bad
[*]gstreamer0.10-plugins-bad-multiverse
[*]gstreamer0.10-plugins-base
[*]gstreamer0.10-plugins-good
[*]gstreamer0.10-plugins-ugly
[*]gstreamer0.10-plugins-ugly-multiverse
[*]gstreamer0.10-schroedinger
[*]gstreamer0.10-x
[*]w32codecs (from Medibuntu repositories)
[/LIST]

Sorry, but I can't say exactly which one is used to reproduce .m4a files...

---

### Post by LowSky on 2007-11-07
did you buy them on iTunes?

If you did they wont play because of stupid DRM

---

### Post by Happy_Man on 2007-11-07
True, but if you rip the files to a thumbdrive or something by dragging and dropping from ITunes interface, they work just fine. :)

---

### Post by BoardDWorld on 2007-11-13
Actually it's something wrong with the version that comes in Gutsy repositories (Exaile 0.2.10). Simply update your repository [HERE]("http://www.exaile.org/downloads"). Exaile 0.2.11 doesn't have this problem. AWESOME PLAYER!!!

---


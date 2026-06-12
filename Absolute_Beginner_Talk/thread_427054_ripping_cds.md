---
title: "ripping cds"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by maitresse on 2007-04-29
I tried using sound juicer to rip some tracks to my pc for use on my mp3 player, but they are too big files.  I can only fit about 7 tracks on it.  Is there some way I can make the tracks smaller.  They are currently coming up as about 40mb each, but I want them a lot smaller.  Can anyone help me!  I am totally new to all this!

---

### Post by Spike-X on 2007-04-29
You're ripping them to uncompressed .wav format. Sound Juicer doesn't support ripping to MP3 that I'm aware of, but I'm sure there'll be something somewhere than can do the job.

---

### Post by eriK-B on 2007-04-29
hey,

you would have to check wether your mp3 player supports ogg(manual, website)
but if it does you can configure sound juicer to rip the tracks
to ogg format this way:
Edit>Preferences> set Output Format to: CD Quality, Lossy(Ogg multimedia)

ogg are around the same size as mp3's (i believe, not entirely sure)
or at least WAY smaller than 40mb :p

good luck, hope this helped

---

### Post by indytim on 2007-04-29
As an added option, you can rip to ogg using SoundJuicer (my preferred app) and do the conversion from ogg->mp3 using SoundConverter (it's in the repositories).

IndyTim

---

### Post by ahaslam on 2007-04-29
Sound Juicer does support mp3 & it's one of the simplest & fastest ways around, ripping directly to mp3. 
To do this you'll need lame installed & a new profile . There's a how to here: [http://ubuntuforums.org/showthread.php?t=189140](http://ubuntuforums.org/showthread.php?t=189140)

;)

---

### Post by 3rdalbum on 2007-04-29
EDIT: Beaten to it by 5 minutes!

Another option:

In Sound Juicer's preferences, make a new profile. Put the following into the Gstreamer pipeline:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=160 ! id3mux
```

Now install lame from the repositories; if there are any "suggested" or "recommended" packages I think you may have to install those too.

Make the profile active and now you should be able to rip straight into MP3 format. I'm surprised that the guy hasn't added this to Automatix.

---

### Post by maitresse on 2007-04-29
> **indytim said:**
> As an added option, you can rip to ogg using SoundJuicer (my preferred app) and do the conversion from ogg->mp3 using SoundConverter (it's in the repositories).

IndyTim

Tried this, and it seems to have worked!  Thanks!

---

### Post by ahaslam on 2007-04-29
:rolleyes:

---

### Post by Metacarpal on 2007-04-29
Another fast and easy, one less step:
install lame and grip.
Once both are installed, grip will rip and encode as mp3.  It also has the option to write the id3 tags so your player shows all the track information.

---

### Post by Purple Grant on 2007-04-30
I am an ultra newbie and just spent the best part of today looking for the plugin to make mp3s work.

this one seems to be the key...
gstreamer0.10-plugins-ugly-multiverse

---

### Post by stchman on 2007-05-08
> **maitresse said:**
> I tried using sound juicer to rip some tracks to my pc for use on my mp3 player, but they are too big files.  I can only fit about 7 tracks on it.  Is there some way I can make the tracks smaller.  They are currently coming up as about 40mb each, but I want them a lot smaller.  Can anyone help me!  I am totally new to all this!

I have a procedure to download the codecs and configure Sound Juicer to rip your audio CDs to MP3s using the LAME encoder for VBR.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

It works.

---


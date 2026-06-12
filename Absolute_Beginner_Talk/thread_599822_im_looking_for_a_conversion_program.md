---
title: "im looking for a conversion program"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-11-01
that can do the following conversions

FROM:

flv
mp3
wav
ogg vorbis
mp4
wma
wmv
mid
midi

TO:

mp3
mp4
ogg vorbis

any program that can do that or most of the froms to the Tos would be good. also, if install isnt sudo apt-get install x or go to add/remove and type x and click install on x it would be great to have install instructions as well
thanks,
antosocialist

---

### Post by andrew.46 on 2007-11-01
Hi,

 Sounds like you are after sox:

[http://sox.sourceforge.net/](http://sox.sourceforge.net/)

 It is a command line utility, not sure if there is a gui frontend for it.

                Andrew

---

### Post by FranMichaels on 2007-11-01
SoundConverter does some of those :)

In Add/Remove (make sure All available applications are shown, the drop-down option in the top right of the window)

Under Sound and Video

Sound Converter

> 
SoundConverter is a simple sound converter application for the GNOME environment. It reads sound files in any format supported by GStreamer and outputs them in Ogg Vorbis, FLAC, or WAV format, or MP3 format if you have the GStreamer lame plugin.
Homepage: [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

As for midi and such, I know Audacious can, provided you have timidity or your soundcard supoorts midi in hardware. Using the disk writer plugin would do the trick...

Audacious and timidity are in Add/Remove as well.

Make sure for audacious you install the plugins-extra, you can go to Synaptic. With the diskwriter plugin, it can output to wav, vorbis, etc. 

:KS

---

### Post by Sable683 on 2007-11-01
I have always had good luck with Audacity... It is in the add/remove on the main menu. Anything that you can load up in Audacity can be exported to an mp3.

~Sable

---

### Post by antisocialist on 2007-11-06
> **FranMichaels said:**
> SoundConverter does some of those :)
thanks that works well and has high quality conversions.
BTW its audacity, not audacious.

---

### Post by Creative2 on 2007-11-07
:D bad programs 

my [http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

here a little video 

[http://it.youtube.com/watch?v=JSPuGnFPMdk](http://it.youtube.com/watch?v=JSPuGnFPMdk)

---

### Post by hyper_ch on 2007-11-07
well, converting from one non-lossless format to another one will reduce quality quite a bit...

---

### Post by Creative2 on 2007-11-07
no all depends from bitrate 

if i have lossless input file , and i re-enconde to another format with high bitrare i will never lost the quality

---

### Post by FranMichaels on 2007-11-08
> **antisocialist said:**
> thanks that works well and has high quality conversions.
BTW its audacity, not audacious.

[Audacious]("http://audacious-media-player.org/") is a different program than audacity. :) 

Audacious is a music player, but instead of choosing output as something like ALSA, you can use the FileWriter output plugin that can write to wav, flac, ogg, and mp3. 

Basically, if it can play the file, it can output it into one of these formats rather than your speakers. 

So, you could load them into a playlist, and just let it play and it would write the files (make sure repeat is not enabled when you do this though ;) )

I wouldn't steer you in the wrong direction :KS

---

### Post by antisocialist on 2007-11-08
i use amarok for music+ipod syncing, and i need a program to convert mainly mp3 and mp4 from my ipod to ogg, for amarok (i prefer using ogg to mpeg) and something to convert my ogg music such as cd rips and jamendo.com music (i use ogg download cuz its faster) to ipod format (mp3), most of the formats i listed as TO's where just 3 or 4 files i had and werent THAT important

---


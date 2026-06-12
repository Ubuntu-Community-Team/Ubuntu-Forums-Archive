---
title: "help with converting"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-15
I have been trying to find a program that is free that can convert mp3s to wav format, but been having trouble.

so I was wondering if someone could convert a song for me from mp3 to wav? I can email it.

---

### Post by forrestcupp on 2008-03-15
In Audacity, you can open an mp3 and export it to wav.

---

### Post by Bruce M. on 2008-03-15
> **RyviusRan said:**
> I have been trying to find a program that is free that can convert mp3s to wav format, but been having trouble.

so I was wondering if someone could convert a song for me from mp3 to wav? I can email it.

Synaptic > soundconverter

Convert audio files into other formats
SoundConverter is a simple sound converter application for the GNOME
environment. It reads sound files in any format supported by GStreamer
and outputs them in Ogg Vorbis, FLAC, or WAV format, or MP3 format if
you have the GStreamer lame plugin.

Homepage: [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

---

### Post by joshrobinson on 2008-03-15
```
sudo apt-get install ffmpeg
```
then
```
ffmpeg -i file.mp3 file.wav
```

---

### Post by Mogurijin on 2008-03-15
Something I really like is [http://www.mediaconverter.org](http://www.mediaconverter.org) . It will convert all sorts of stuff for you. However, you might want an actual program instead of a Web app. You can download the media converter, but I doubt they have a Linux version.

---

### Post by alecz20 on 2008-03-16
> **Bruce M. said:**
> Synaptic > soundconverter

Convert audio files into other formats
SoundConverter is a simple sound converter application for the GNOME
environment. It reads sound files in any format supported by GStreamer
and outputs them in Ogg Vorbis, FLAC, or WAV format, or MP3 format if
you have the GStreamer lame plugin.

Homepage: [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)
SoundConverter does not work for me!

I load a file, I choose output to be .wav, I click Convert, and all top buttons become grayed out and nothing happens. CPU usage is at zero, and the progress bar is stuck.
I can cancel or pause, but I cannot convert, any ideas?

---

### Post by theRightNee on 2008-03-16
have you tried this several times? same thing happened to me one time, and i just canceled and restarted conversion and worked like a charm. also make sure you have all the codecs installed (only GStreamer works)

---

### Post by Bruce M. on 2008-03-16
> **alecz20 said:**
> SoundConverter does not work for me!

I load a file, I choose output to be .wav, I click Convert, and all top buttons become grayed out and nothing happens. CPU usage is at zero, and the progress bar is stuck.
I can cancel or pause, but I cannot convert, any ideas?

Why not try this:

> **joshrobinson said:**
> ```
sudo apt-get install ffmpeg
```
then
```
ffmpeg -i file.mp3 file.wav
```

Personally I have never converted a file, no need to.

I put **mp3 to wav** in Synaptic and found a lot.  Just posted one here as an option.

---


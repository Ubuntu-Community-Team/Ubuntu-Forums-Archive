---
title: "DVD Audio Ripping program?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Prozzy on 2006-01-15
Okay, Im looking for some program to extract/rip my audio from my dvd.

In windows i used ImToo DVD Audio Ripper, and it worked nice and easy. I could cut by chapters or by user defined time stamp.

I didnt have any luck with google so hope somebody might be able to help me. 

So im looking for something similar to ImToo DVD Audio Ripper, a program that can extract the audio track from a DVD and split it default by chapters/titels.

- Greets Prozzy

---

### Post by morphodone on 2006-01-15
you might try dvdrip

it should be in the repositories

here is the [site]("http://www.exit1.org/dvdrip/")

---

### Post by ufa on 2006-02-26
I cant do ir with dvd::rip...any one have a tutorial or another program?

---

### Post by nalmeth on 2006-02-26
sudo apt-get install acidrip
I don't know how to do what you're looking for, but get avidemux aswell, because you could at least take the ripped file from the dvd and edit it with avidemux, or maybe audacity. Keep looking though, there might be something more useful out there

---

### Post by wmcbrine on 2006-02-26
I've used MPlayer to do it, like so:

mplayer -dumpaudio -dumpfile file.ac3 dvd://1

If you're working with PCM audio, or in any case if you want a WAV, you might do it this way instead:

mplayer -ao pcm -vo null -vc dummy dvd://1

(makes "audiodump.wav"). Add "-chapter 1" etc. as needed (see the mplayer man page for more).

Oh... I'm assuming here that you're talking about the audio tracks on a regular DVD. I have no idea about audio DVDs (DVD-A).

---

### Post by ufa on 2006-02-26
Easy way with dvd::rip

2.8.8 Create a WAV file

If you just want to have a WAV file from your music DVD, e.g. to burn it on a traditional audio CD: select the correspondent audio track and select the Create WAV from selected audio track item in the Operate menu. If the audio track is PCM already, it will be passed through, otherwise a correspondent conversion resp. downmix will be applied.

If your project is in chapter mode, you'll get one WAV file per chapter.

---


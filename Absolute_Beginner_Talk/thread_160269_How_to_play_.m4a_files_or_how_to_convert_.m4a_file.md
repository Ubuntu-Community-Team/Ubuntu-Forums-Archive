---
title: "How to play .m4a files or how to convert .m4a files to .mp3???"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by dmbatcu on 2006-04-14
I have a bunch of music I backed up from my iTunes collection, which is not DRM-protected. How can Iconvert my .m4a's to a more Kubuntu-suitable file such as mp3?

---

### Post by gingermark on 2006-04-14
In Konsole type 'sudo apt-get install gstreamer0.8-faad'.

You'll need to enable extra repositories beforehand though. If you haven't already done that, type 'kdesu kate /etc/apt/sources.list' and remove the '#'s before the lines beginning "deb". Save the file, then do "sudo apt-get update".

---

### Post by ncappel1 on 2006-04-14
In general, converting between audio formats will have adverse effects on the sound quality of the music file. If you really want to go ahead and do it, "Sound converter" will do the job, you can download that from synaptic. there is another nice nautilus script whic hI havn't used much, but seemed to work pretty well, "audio-convert"

---

### Post by JeevesBond on 2006-10-29
Nice replies they helped a lot. Had one problem converting to mp3's though: didn't have all the packages installed.

So if SoundConverter lets you select output to mp3 but when you select some files, then start nothing happens. Make sure you have: gstreamer0.8-tools installed!

If this isn't installed the converter fails but doesn't display an error. In fact it acts as though it's converted all the files!

---

### Post by hotani on 2006-10-31
I'm trying to convert some very high quality m4a files to mp3 to get the filesize down a bit, but the mp3 option is not available in soundconverter. Using ogg for now, but eventually i'd like to go to mp3 so they'll play on yon ipod. Ideas?

---


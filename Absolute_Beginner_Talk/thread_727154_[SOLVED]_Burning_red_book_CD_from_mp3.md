---
title: "[SOLVED] Burning red book CD from mp3"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2008-03-17
Hello Everybody,

I would like to burn a red book CD from a series of MP3 files. I read in a magazine article that K3B does that automatically. I opened a new Audio CD project but when I try to drag & drop the MP3 files, K3B says: 

[I]"Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project."[/I]

I then used Sound Converter to convert the MP3 files to WAV but K3B still gives me the very same error message when I try to drag & drop the WAV files in.

Can anyone shed some light on what I'm doing wrong here?

Many thanks,

Charlie

---

### Post by ajgreeny on 2008-03-17
Not sure what a red book CD is but when I use k3b to burn an audio CD it is just a case of choosing New Audio CD from the start screen and navigating to the folder where the wav or mp3 files are and clicking them, I don't even need to drag, though that may be because I have my system set up to do things on a single click, not a double click.  Have you got the libk3b2-mp3 library installed, if not get it from the repos with synaptic or apt-get.  I can't imagine why the problem with wav files, however.

---

### Post by bruce89 on 2008-03-17
Saying as this is likely to be a GNOME environment, Serpentine can make audio CDs (Sound & Video>Serpentine). In order for it to be able to convert MP3s, you need to install *gstreamer0.10-plugins-ugly-multiverse*.

---

### Post by Charlie Chick on 2008-03-21
Thany you both for your replies. 

Red Book refers to the Philips / Sony standard for a finalised audio CD with a permanent table of contents (TOC). There are different colour books for different types of CD e.g Orange Book for CD-ROM.

After checking that I already had gstreamer0.10-plugins-ugly-multiverse already installed I tried Serpentine (which I admit that I had completely forgotten about) and it worked! I now have a Red Book audio CD from the original MP3 files which I can play on any CD player in the world.

Thanks again, helpful Ubuntu people!

---


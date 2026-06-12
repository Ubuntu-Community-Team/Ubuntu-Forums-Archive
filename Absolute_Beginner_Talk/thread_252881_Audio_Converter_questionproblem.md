---
title: "Audio Converter question/problem"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-09-07
I have installed the audio converter app with the .deb package that I found On this page: [https://savannah.nongnu.org/projects/audio-convert](https://savannah.nongnu.org/projects/audio-convert)

After package installer did its thing, it said it was installed, but when I right click on a .mp3 or .ogg file, I get absolutely no convert option at all. Any ideas ? 

Doug

---

### Post by harlan on 2006-09-07
Try with audacity
$ sudo aptitude install audacity
For mp3 you will need lame. Now there isn't a deb package, but search lame.rpm in google and convert it in a .deb one
$ sudo alien lame.rpm
and install it
$ sudo dpkg -i lame.deb
audacity needs you to show the path to the mp3 library.Open audacity,go to edit/preferences and click search library

---

### Post by Sweet Spot on 2006-09-07
I've got all the LAME stuff I need, and I'd rather not install Audacity becuase it works like crap for me. I've tried using it to create a vocal track on a file I made which is a Radiohead cover (Big Boots) and the vocals (mine) just didn't work at all. They sounded like a complete mess (several octaves down, pitch all messed up and artifacting like crazy). 

I don't like Audacity on this platform at all. Besides, I think that Audacity is a bit of overkill for a simple transcoding job, no ?

Doug

Edit: perhaps someone can tell me a command line which will do the job ? I want to convert from Ogg to Wav. Yes, I know this is technically pointless as far as quality goes. I am VERY familiar with the whole transcoding process, losing bits etc etc... It's just that I want to use Ogg files as system sounds, and only .wav files seem to be valid for such a thing.  It's not like I'm doing this for music files I want to listen to, I'd never do that to myself.

---

### Post by harlan on 2006-09-08
you need vorbis-tools,if you don't have it installed yet
$ sudo aptitude install vorbis-tools
if the .ogg file is in /home/user/ogg/file.ogg 
$ oggdec /home/user/ogg/file.ogg

---

### Post by Sweet Spot on 2006-09-08
Thanks for trying to help. I already have vorbis tools installed. I actually probably have all the audio codecs and tools needed since I used Automatix, plus the fact that if it didn't cover something I use (.shn etc.. ) I'd probably have installed it by now. That isn't the problem, and I'm trying to find out what it is which isn't allowing the convert option to pop up upon right clicking of a music file. 

Doug

---


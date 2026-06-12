---
title: "WMVHD (VC-1)  With 5.1 sound"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by crono141 on 2007-10-29
I am having a problem.  I'm trying to set up linux as a media center on a laptop to talk to my windows server which is housing all my content.  I've ripped probably 30 or so DVDs with the WMVAP profile (VC-1 codec) for use on my Xbox360.  Problem now is I can't get any of these files to play properly on my linux box.

I have amd64 (with w64codecs) and all the other suggested av codecs that are referenced in countless other threads on here.  With the default Ubuntu player, I get no sound, no video, and it does a search for a compatible playback codec (none is found).  With VLC, I can get video, and it recognizes an audio stream, but it won't play the audio stream.

I'm pretty sure my problem is with the audio, because I can get video to work in some form or another consistently.  Anybody have any ideas? :confused:

EDIT:  I think I have it figured out.  The audio is all in 5.1 surround, but I only have a 2 channel sound mixer on this PC.  Is there a way to downmix 5.1 to 2 channel audio on linux?

---

### Post by crono141 on 2007-10-30
I have another update.  VLC is showing 0 bits decoded for audio, and it only gives me the option to choose track 1 audio or no sound in the audio menu (no other options show up)

The audio is encoded in WMA10, and even 2 channel WMA10 doesn't play.  Is there a WMA10 decoder for linux?

---

### Post by FranMichaels on 2007-10-30
Hello, I searched the forums, does this help you?

[http://ubuntuforums.org/showthread.php?t=537065](http://ubuntuforums.org/showthread.php?t=537065)

Specifically the last post.

Would you consider re-ripping your DVDs? 
I personally avoid proprietary formats for backups for that reason. There is a good chance it won't work or not work to its fullest on another OS or player. If the vendor drops support you are out of luck using it in future... :(

---

### Post by Octagonal on 2007-10-30
This is one of the reasons I went from 64bit to 32bit Gutsy.  I couldn't get WMVHDs to play properly.  As WMVs are really the only viable way to stream HD movies to your xbox 360 (mp4s are limited to 4GB and no 5.1 surround sound support).  If you can get this to work I am very interested in knowing how...

You may want to try 32bit mplayer...

this link may help...  I would have tried this before switching to 32 bit if I knew about it at the time. 
[http://ubuntuforums.org/showthread.php?t=432642&highlight=mplayer+32+bit](http://ubuntuforums.org/showthread.php?t=432642&highlight=mplayer+32+bit)

---

### Post by crono141 on 2007-10-30
Thanks for the responses.

Re-ripping the DVDs is not an option, as the only way to get 5.1 audio through the 360 and Media Center Extender is to use WMV with WMA10pro.  I tried installing smplayer, but it didn't have a codec (wmap) to decode the audio.

I notice that wma9 is fully supported.  I'm a linux noob, so I don't know the process, but is it not possible to get wma10 working is a similar fashion?

And is this a 64bit problem more than a linux problem?

I'll try tweaking it somemore and installing mplayer32.  I'll let you know how it goes.

---


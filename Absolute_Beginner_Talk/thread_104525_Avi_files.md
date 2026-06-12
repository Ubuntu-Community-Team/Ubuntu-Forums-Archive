---
title: "Avi files"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-12-16
What are Avi files, please?

trying to download some anime files. No luck. is that because Avi are only windows compatible?

Anyone, who may be familiar with Hikaru no go may be able to tell me where i can download

thanks 

--
sophtpaw

---

### Post by Pablo_Escobar on 2005-12-16
Avi are perfectly playable on Linux boxes. Check if You have w32codecs installed  -> I'd recommend the PLF repo.

---

### Post by sophtpaw on 2005-12-16
[QUOTE=Pablo_Escobar]Avi are perfectly playable on Linux boxes. Check if You have w32codecs installed  -> I'd recommend the PLF repo.[/QUOTE]


Gracias Pablo!

I let Synaptic install w32codecs. Surprised that i hadn't already done it before. I think as i recall when i switched from Hoary to Breezy there was a problem with the ubuntuguide which is maybe why i didn't install them.

I hope that explains why totem was crashing when i was trying to play the Avi files. 

--
sophtpaw

---

### Post by Pablo_Escobar on 2005-12-16
For Totem, I'd recommend the xine engine - apt-get totem-xine :)

---

### Post by pizzach on 2005-12-16
[QUOTE=sophtpaw]What are Avi files, please?
[/QUOTE]

To round out this article, a slight description of avi files:

Avi files are a container format.  A very old one at that.  They are often found on windows, but are not restricted to it.  As a container format they can contain different types of codecs for streams of audio and video.  (An example would be divx video or wav audio vs mp3 audio)

```

ogg_container_format_file.ogg
___________________________________________________
|                 video                    
|__________________________________________________|
|       audio_eng.mp3 | audio_ja.wav       
|__________________________________________________|
|            subtitles (english)           
|__________________________________________________|

```

Hehe.  Just looking for an excuse to do some line art. It's supposed to be a box with different sections by the way. :)

For Japaninimation I prefer mkv or ogg.  Just because they can have both the english and japanese audio streams and removeable subtitles.

---


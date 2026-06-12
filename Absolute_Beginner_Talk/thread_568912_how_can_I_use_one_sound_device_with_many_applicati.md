---
title: "how can I use one sound device with many applications?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by lian1238 on 2007-10-06
Hi,
When I have a music player playing a song, I cannot watch a movie with sound coming from that same device. What can I do so that I can?
Thanks in advance.

---

### Post by luisromangz on 2007-10-06
What programs are you using? There are several sound systems for linux, OSS, ALSA, Arts, ESD, etc. Some of them can use the others (for example, Arts can use ALSA as output).

If two programs use different sound systems, both systems will try to use the same system resourse, so you need all your sound apps using only one sound system. Think of it just like a printer queue, you have only one printer and each printer wants to use it, so the printe qeue puts a bit of order there, as programs don't use the printer directly but the queue. But if you had two printer queues, the problem would get back.

Make sure your programs use the same audio backends.

---

### Post by lian1238 on 2007-10-06
I'm using an Acer laptop. The headphones jack doesn't work for me with Feisty Fawn, so forget about that. In the volume control, There are two devices: HDA Intel (ALSA) and Realtek ALC883 (OSS Mixer). It seems, whatever device I chose in the Sound Preferences for Music and Movies, it plays from the internal speakers.
So, my problem is like this: for example, I have Rhymthmbox Music Player playing a song, works fine. Then I open a movie with VLC player, no sound... I close both of them. Then I open the movie again, there is sound! Any thoughts?

---

### Post by HermanAB on 2007-10-06
I guess you don't know Jack:
[http://jackaudio.org/](http://jackaudio.org/)
:)

Also see this:
[http://del.icio.us/url/4b30c0ac8c496aa36f4cc49ba4e1b5cb](http://del.icio.us/url/4b30c0ac8c496aa36f4cc49ba4e1b5cb)

Have fun!

Herman

---

### Post by HermanAB on 2007-10-06
You should also look at sox:
[http://www.linux.org/lessons/short/sox/index.html](http://www.linux.org/lessons/short/sox/index.html)

and streaming MP3 with Edna:
[http://www.aeronetworks.ca/ogg2mp3-howto.html](http://www.aeronetworks.ca/ogg2mp3-howto.html)

and making your PC talk back at you or read your email for you:
[http://www.aeronetworks.ca/text-to-speech-howto.html](http://www.aeronetworks.ca/text-to-speech-howto.html)

Hours of fun!

Herman

---

### Post by lian1238 on 2007-10-06
thanks! I think this is what I need. I'll have to try.

---

### Post by lian1238 on 2007-10-06
alright, I've installed JACK. Now I don't know what to do.

---

### Post by lian1238 on 2007-10-06
whoa wait! It's working! I don't know if this is the work of JACK or not.. but in VLC, I changed the audio output module to "default", and audio plays along with the sound from other applicatoins. If this is JACK's doing, please do say so. If it isn't, I'll try to uninstall JACK.. although I haven't found any easy way to uninstall stuff in ubuntu yet.. still learning as I go. :D

---


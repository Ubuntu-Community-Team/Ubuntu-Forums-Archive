---
title: "I want to choose bitrate 256 kb in Sound Juicer."
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-01
My mp3-player manufacturer recommended this program to extract music from CDs to mp3 files using open source CDex.
But it seems CDex doesn't exist for Linux so I thought of using Sound Juicer. But in SJ I can't choose what bitrate I want to convert to. Also I m want it in Ogg, but there's only 2 options for Ogg

Sound Juicer
Output Format: CD Quality, Lossy (Ogg multimedia)
Output Format: Voice, Lossy (Ogg multimedia)

In CDex I converted my CDs to 256 kb format how can I obtain the same quality with Sound Juicer?

---

### Post by crispy_420 on 2007-02-04
In sound juicer to edit -> preferences.

Near the buttom under format select edit profiles.

Add new profile.

> Profile Name:   CD Quality, Lossy (mp3)
Profile Description:   (put whatever here)
GStreamer Pipeline:    audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=256 ! id3v2mux
File Extension:   mp3

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

[http://www.ubuntuforums.org/showthread.php?t=22010&highlight=sound+juicer](http://www.ubuntuforums.org/showthread.php?t=22010&highlight=sound+juicer)

[http://www.ubuntuforums.org/showthread.php?t=957&highlight=sound+juicer](http://www.ubuntuforums.org/showthread.php?t=957&highlight=sound+juicer)

[http://www.ubuntuforums.org/showthread.php?t=295698&highlight=sound+juicer](http://www.ubuntuforums.org/showthread.php?t=295698&highlight=sound+juicer)

---

### Post by jingo811 on 2007-02-05
tnx for the links I'll read them through when I got more time.
Also I wanted to experiment converting my CDs with the patent free codec Ogg.  Do you have a quick fix for doing that in bitrate 256 kb/sec?

The previous solution you gave me that's involving the patented format mp3 right?
[http://en.wikipedia.org/wiki/MP3](http://en.wikipedia.org/wiki/MP3)

---

### Post by crispy_420 on 2007-02-05
Sorry read you wrong, thought you wanted mp3.

Here is a link for ogg:

[http://www.ubuntuforums.org/showthread.php?t=187480&highlight=sound+juicer+ogg](http://www.ubuntuforums.org/showthread.php?t=187480&highlight=sound+juicer+ogg)

---

### Post by jingo811 on 2007-02-06
hmm so basically I use this instead and add bitrate=256 like in your example?
> audio/x-raw-int,rate=44100,channels=2 ! vorbisence name=enc quality=0.5 [COLOR="Red"]bitrate=256[/COLOR] ! oggmux

---


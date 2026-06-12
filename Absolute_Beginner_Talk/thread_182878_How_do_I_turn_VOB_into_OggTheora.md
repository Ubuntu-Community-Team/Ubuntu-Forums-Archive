---
title: "How do I turn VOB into Ogg/Theora"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by nexist on 2006-05-26
IT is driving me batty, I've been trying to get the proper syntax for either transcode (which I don't think supports Ogg/Theora, but I could be wrong) or ffmpeg.  I tried to install vive as per another thread, but that had issues with zlib (which synaptic showed as being installed).

WHat I would like, is the syntax to cause ffmpeg to read multiple VOB files and provide me with a shiny Ogg/Theora file (actually, I would rather a lossless codec).

Can someone help me.  I am more than happy with the default settings that I have from the VOB files.

---

### Post by nexist on 2006-05-29
I've been trying to use DVD:Rip (since this post), but I get an audio merge error.

Job ' Merging audio - title #1, audio track #1 failed.

Details:
Ubuntu Linux Dapper Drake 6.06
Gnome desktop: 2.14.1
dvd::rip: 0.52.5
transcode 1.0.2 (0.0ubuntu2)

---

### Post by richbarna on 2006-05-29
I am on Dapper Drake, and to rip dvd's I use k9copy to rip the dvd to the desktop, then I use dvdshrink with wine to compress the files to 4.4 Gig to create a burnable dvd.

Also I have just dragged all the .vob files out and burnt them directly to a dvd and they play ok in my dvd player.

I find no need to convert to any other format.

If you can tell me exactly what you need the files for, or why you need an ogg/theora format specifically, I can check out some software.

---

### Post by ametade on 2006-05-29
Check the following package. It's only available for dapper, but you can try to make a backport:

[http://packages.ubuntu.com/dapper/graphics/ffmpeg2theora](http://packages.ubuntu.com/dapper/graphics/ffmpeg2theora)
[http://www.v2v.cc/~j/ffmpeg2theora/index.html](http://www.v2v.cc/~j/ffmpeg2theora/index.html)

I'm using it to convert video files (including unencrypted .vobs) to .ogg theora files with success.

---

### Post by richbarna on 2006-05-29
I just read about Theora/ogg on wikipedia, is there likely to be a dvd player that will support this format ?

---

### Post by nexist on 2006-06-09
[QUOTE=richbarna]I just read about Theora/ogg on wikipedia, is there likely to be a dvd player that will support this format ?[/QUOTE]

I am not planning on playing it on a DVD player. I watch movies on my laptop & I hate lugging around my DVD's when I travel.

---

### Post by nexist on 2006-06-09
[QUOTE=ametade]Check the following package. It's only available for dapper, but you can try to make a backport:

[http://packages.ubuntu.com/dapper/graphics/ffmpeg2theora](http://packages.ubuntu.com/dapper/graphics/ffmpeg2theora)
[http://www.v2v.cc/~j/ffmpeg2theora/index.html](http://www.v2v.cc/~j/ffmpeg2theora/index.html)

I'm using it to convert video files (including unencrypted .vobs) to .ogg theora files with success.[/QUOTE]

I've used that to convert some WMV files, but there seems to be an issue with syncing the audio to the video.  They play fine in Windows systems, but they lag out of sync on Linux.

---

### Post by Dragonfire on 2006-06-09
try using K3B.

it's great for this, and so is sound juicer.

---


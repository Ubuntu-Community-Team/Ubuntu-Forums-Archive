---
title: "No video with WMV files"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by AndyC_772 on 2005-11-27
Apologies if this one is answered in a FAQ somewhere, but...

When I try to play WMV files, Totem launches and I get sound, but no video.

Any suggestions please?

---

### Post by Kimm on 2005-11-27
Try downloading Mplayer and w32codecs, then plat the file with MPlayer (duh), might work, cant tell you for sure though

---

### Post by AndyC_772 on 2005-11-27
I've downloaded mplayer-586, which correctly plays video - thanks :)

Only thing is, it plays in a tiny window, and resizing it just adds a border around the edge. Is there a way to make it scale the image up to a more reasonable size?

Ta
Andy

---

### Post by Turtle.net on 2005-11-27
I had this problem with mplayer, but never with xine and vlc (I only use these two softwares for all the videos format).
My preference goes to VLC but xine is very good also.
Try them and let us know ;)

---

### Post by rizzyc on 2005-12-29
i'm having trouble finding/installing mplayer.. i'm a newbie at this
i'm typing sudo apt-get install mplayer but it says it doesnt exist..
i'm trying to get my wmv files to play

---

### Post by rharris on 2005-12-29
Andy:

Go to mplayer's preferences and select the video tab. Once there change the selection to "xv" this worked for me as far as resizing the playback size.

Rob

---

### Post by rizzyc on 2005-12-29
[QUOTE=rharris]Andy:

Go to mplayer's preferences and select the video tab. Once there change the selection to "xv" this worked for me as far as resizing the playback size.

Rob[/QUOTE]
I was not able to download mplayer for some reason and my add apps button disappeared. BUT i was able to dl some deb file and install it with the help of a wikipedia site. (Y) Totem player showed video and sound VLC only showed sound.
Thanks for the help though

---

### Post by Turtle.net on 2006-01-02
[quote=rizzyc]i'm having trouble finding/installing mplayer.. i'm a newbie at this
i'm typing sudo apt-get install mplayer but it says it doesnt exist..
i'm trying to get my wmv files to play[/quote]
Hi,
I think you should add extra repositories [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")
and have a look to 
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

You can also try to install xine-ui (perfect for wmv files)
And be sure to install w32codecs
Good luck ;)

---


---
title: "Rythmbox Problems"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by thomasaaron on 2006-10-04
I'm having difficulty with Rythmbox.
All of my music files are on an external hard disk.
They were all downloaded from CDs or from MSN music in the past.
All of them were previously playable on Windows Media Player.

I've downloaded the following codecs:

gstreamerx.x-plugins
gstreamerx.x-plugins-multiverse
gstreamerx.x-ffmpeg

Of course, the downloads included a bunch of other files as well.

In Beginning Ubuntu Linux (Keir Thomas), he said those would cover pretty much all music formats.

When I try to play one of my music files (which are in .wma format) I get an error message saying that the file is not a streaming audio file.

Any ideas?

Best,
Tom

---

### Post by whizbaby on 2006-10-04
Only method for me to listen/view .wma is
install totem-xine and libxine-extracodecs and w32codecs (of course uni-/multiverse is enabled in your /etc/apt/sources.list?).
and use totem for these files.
EDIT:
Oh, and I also have all the gstreamer- *good*  *bad* and *ugly* codecs installed!

---

### Post by zerodogma on 2006-10-04
From a nOOb:
Correct me if I am wrong, but but trying to play/library .wma files is a real pain -- if I try and play them, they are opened up in Totem.  I am currently converting all of my .wma files to .mp3 (or you could use .ogg).  If you still have your M$ partition or drive (like I do), you could convert them over using your favorite conversion program, and then you should be home free.  I feel a little dumb now not knowing that all of my .wma files would be such a pain in the long run ---- live and learn.

---

### Post by whizbaby on 2006-10-04
> **zerodogma said:**
> real pain -- if I try and play them, they are opened up in Totem
Don't understand how this can 'hurt' somebody so much ...

---

### Post by gvgerman on 2006-10-04
Being a noob and a XP user, EasyUbuntu was the most comfortable way for me to get Rythmbox working with *.wma files.
Look here:  [http://www.ubuntuforums.org/forumdisplay.php?f=86]("http://www.ubuntuforums.org/forumdisplay.php?f=86")

---

### Post by zerodogma on 2006-10-04
> **whizbaby said:**
> Don't understand how this can 'hurt' somebody so much ...
Its not a matter of .wma files opening in Totem 'hurting' or being 'bad'.  If thomasaaron is trying to do the same thing I am, he will need to covert the files to a format that [Rhythmbox]("http://www.gnome.org/projects/rhythmbox/index.html") will catalog and play so everything is 'nice and neat' so to say (one library for all music).
Maybe I am still looking at this the wrong way...??? I have only just started using Ubuntu (or ANY Linux for that matter) and am doing the crash course thing.

P.S. - You pros here on the forums do a FANTASTIC job of helping new converts get things right.  Kudos to the community!

---

### Post by whizbaby on 2006-10-04
> **zerodogma said:**
> one library for all music
Impossible for me: some radio streams only provide real-media so I need RealPl for them, some others come only in M$ proprietary format so I play them in totem. Because I hate the look-and-feel of RPL (where the hell is my playlist?) I use xmms (and perhaps eclair in the future) to listen to mp3/ogg.

---


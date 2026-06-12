---
title: "Rhythmbox, Ogg Streams, and Buffering"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Zack Replica on 2007-03-01
This is my first week with a Linux computer of any kind (I'm running 6.10 Edgy Eft), and I'm remembering what feeling stupid, feeling overmatched by things that are probably simple, is like.

One of my highest priorities being Internet radio, I found a couple of stations that play ogg streams, the CBC in Toronto and an avant-garde music station in Seattle, and opened them in Rhythmbox.  In both cases, the stream would start, play a few minutes, and then stop.  Rhythmbox would indicate that it was buffering the stream, but it couldn't resume playing unless I clicked the play button to make it pick up the stream once more.  And then the same sequence of events would start all over again.

Am I missing something obvious, like a setting in Rhythmbox or at the Ubuntu system level that needs to be tweaked?  I have a fast AT&T/Yahoo DSL connection, so insufficient bandwidth shouldn't be an issue.

---

### Post by luke411 on 2007-03-01
DId you download the additional Gstreamer codecs? They are not included in the original installation due to copywrights and all of that. YOu need them though in order to play dvd's, mp3. mp4, etc. YOu can get them and read about them here.
[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

---

### Post by Zack Replica on 2007-03-01
> **luke411 said:**
> DId you download the additional Gstreamer codecs? They are not included in the original installation due to copywrights and all of that. YOu need them though in order to play dvd's, mp3. mp4, etc. YOu can get them and read about them here.
[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

I haven't yet, and probably will, but I thought ogg was a native Ubuntu audio format.  Why is the addition of codecs necessary for what I was trying to do?

---

### Post by doclivingston on 2007-03-02
It's a known bug in GStreamer, not being able to handle chained ogg correctly, [http://bugzilla.gnome.org/show_bug.cgi?id=320984](http://bugzilla.gnome.org/show_bug.cgi?id=320984)

---


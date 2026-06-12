---
title: "Samsung YP-K3 Not Mounting"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-05-01
Hi,

Im running Ubuntu 7.04 64 bit ...... when I attach my Samsung MP3 player to a usb port, I can see it under system>preferences>hardware information>computer>usb 2.0>etc etc. However I can not connect to it to be able to copy files to or from it ..... not seing it in the media file either...any suggestions gratefully accepted

---

### Post by steve-shinn on 2007-05-01
...

---

### Post by pragmatine on 2007-05-07
The Samsung YP-K3 uses the proprietary [MTP]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol") protocol, and so is not very well supported under Linux (there is libmtp but this is still in early development and the version in Ubuntu does not support the YP-K3).

BUT all is not lost - there is a Korean firmware version which provides USB Mass Storage so you can mount it like an external USB drive, plus it also provides Ogg/Vorbis support.

For more info and instructions take a look at the Gentoo forums [here]("http://forums.gentoo.org/viewtopic-t-556945.html"). I just went through the process of upgrading my YP-K3 today, so post back if you run into any trouble.

---

### Post by steve-shinn on 2007-05-08
Followed the instructions .... panicked at first when the menu was in Korean ..... sorted taht out though and now it mounts automatically in Ubuntu.....well chuffed .... thanks

---

### Post by pragmatine on 2007-05-10
No probs - I freaked out too the first time when the screen went white, but perseverance pays off, and now I have everything I could want in an mp3 player - usb mass storage support, ogg playback suppport,in built radio, and it looks better than an ipod - I couldn't be happier, so I am glad to share the fun.

---


---
title: "Rhythmbox Music Player"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by makinasvp on 2007-04-16
I'm using Ubuntu Feisty at this point. I have a quick question.
Is anyone using Rhythmbox Music Player? I have a little problem...
For some reason, when I use Amarok in order to play my music, the sound quality is near perfect.
But when I play my music with Rhythmbox Music Player, I hear static sounds... The quality is great.
Is that happening to anyone else? And if there's a fix for it, please discuss how. Thank you in advance... :)

---

### Post by rufius on 2007-04-16
Its probably whatever playback codec you're using. I think the default for Rhythm Box is gstreamer, you may want to add some of the codecs. "apt-cache search gstreamer" shows both gstreamer 0.8 and 0.10. I'm not sure which is better but I've had decent luck with 0.10. You can check what version is installed with the following: ```
dpkg --search gstreamer
```.

Hope that helps! :-D

---

### Post by makinasvp on 2007-04-16
I have gstreamer .10 installed... And it's still doing that...

---

### Post by makinasvp on 2007-04-16
bump

---


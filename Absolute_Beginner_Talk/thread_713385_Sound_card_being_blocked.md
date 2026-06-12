---
title: "Sound card being blocked"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by thecow on 2008-03-02
If a program is using my sound card, it blocks all other programs from using it.  For instance, if I am looking at a youtube video and want to also have my mp3 player program open at the same time, it wont allow this.  Frequently Id like to have multiple things open that have sound, like watching amovie and also have an mp3 player open.  So if I am doing work I can pause the movie for a period of time and start listening to music.  However this is impossible, it gives me an error that says a program is blocking the use of my sound card.

This also causes problems in weird ways.  For instance sometimes I will have nothing open that is using my sound card and I will try to open my mp3 player and it will say a program is blocking my sound card.  So clearly this situation is not reasonable.  Is there some way I can fix this?

---

### Post by julian67 on 2008-03-03
> **thecow said:**
> If a program is using my sound card, it blocks all other programs from using it.  For instance, if I am looking at a youtube video and want to also have my mp3 player program open at the same time, it wont allow this.  Frequently Id like to have multiple things open that have sound, like watching amovie and also have an mp3 player open.  So if I am doing work I can pause the movie for a period of time and start listening to music.  However this is impossible, it gives me an error that says a program is blocking the use of my sound card.

This also causes problems in weird ways.  For instance sometimes I will have nothing open that is using my sound card and I will try to open my mp3 player and it will say a program is blocking my sound card.  So clearly this situation is not reasonable.  Is there some way I can fix this?

This should be fixed in Hardy which will use pulseaudio instead of esd. This means multiple applications will be able to use your soundcard at the same time and you'll also be able to do nice things like set the volume per application.

---


---
title: "How do I schedule streams from radio stations to be recorded?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by jEsus_extRact on 2008-03-23
I've googled and searched the forums for an answer but can't find one. Which is weird because every question/problem I have had google has answered. I used to schedule streams to record from an online radio stream ktrh.com in windows. I haven't come across a way to do this in Ubuntu. I tried streamripper/streamtuner but the stations I listen to aren't on the list (Talk). I don't know how to get the stream url to put it in streamtuner. The show I listen is four hours long and most of the threads on recording radio streams deal with music. Is there a guide to recording radio ktrh.com in particular, I may have missed or this is a lost cause?

---

### Post by cuby on 2008-03-24
hello,
Its not very elegant, but I've managed to create a comand line to control vlc to do this:
```
vlc  http://[adress] :demux=dump :demuxdump-file="/home/location/filename.mp3" -I dummy  &
```

You can schedule this to start on cron, but you have to stop it, killing the process yourself.
Hope it helps.

---


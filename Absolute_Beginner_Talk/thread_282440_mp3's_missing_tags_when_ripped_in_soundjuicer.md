---
title: "mp3's missing tags when ripped in soundjuicer"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-22
am i missing something on my pipeline? for some reason my tags aren't showing up when i rip cd's in soundjuicer. here's my pipeline.

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux
```

maybe i'm missing a dependency?

---

### Post by shanepardue on 2006-10-23
any ideas?

---

### Post by shanepardue on 2006-10-23
last bump! any help is great!

---

### Post by CatKiller on 2006-10-23
You could try id3v2mux at the end instead, although I really don't know much about any of this yet.

---

### Post by redDEADresolve on 2006-10-24
bump agian.
I'm dying to know also. Not in any mp3 guides I've read so far.

---


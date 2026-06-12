---
title: "Find and play music command"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-05-08
```
find ~/ -name songname.foo | xmms
```
Please help?  How do I get xmms to play what I just found?

---

### Post by ruzle0 on 2006-05-08
try the same but with -p (play)
```

find ~/ -name songname.foo | xmms -p
```

---

### Post by ruzle0 on 2006-05-08
ok I've had a play and i see some of your problems, my command line skills are nothing to shout about, and hopefully someone with some sense can make this more elegant.

basically this builds an m3u playlist for xmms to play
```

 echo "#EXTM3U" > testpl.m3u;find ./mp3/ -name *.mp3 >> testpl.m3u; xmms -ep testpl.m3u

```
i'm sure someone who knows what they are doing, can do it without building a file to pass to xmms and just use cat and pipes or something
this is also limited as it goes by the file name and not the id3 tag of the file.
the -ep option after xmms will make it so it appends to the playlist and plays, get rid of 'e' if you want to completley replace the play list.

---


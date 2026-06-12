---
title: "Record Audio Streams from Internet ?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-19
Anyone know a program to do this in Ubuntu ?   Thanks  :)

---

### Post by richbarna on 2006-06-23
[QUOTE=Drakkor]Anyone know a program to do this in Ubuntu ?   Thanks  :)[/QUOTE]
Try this :-
[http://shstream.sourceforge.net/]("http://shstream.sourceforge.net/")

---

### Post by Kouya on 2006-06-24
use can try mplayer: eg. in terminal type 

```
mplayer -cache 10000 -dumpstream -playlist  http://boss.streamos.com/wmedia/swn/oneplace/wm/bh/bh20060623.wax -dumpfile save.mp3

```

---

### Post by airzer0 on 2006-06-24
i use mms with gstreamer
so sudo apt-get install xmms
then sudo apt-get install streamtuner

---

### Post by Drakkor on 2006-06-24
Thanks all, but I was trying to record Pandora, seems there's no URL.

---


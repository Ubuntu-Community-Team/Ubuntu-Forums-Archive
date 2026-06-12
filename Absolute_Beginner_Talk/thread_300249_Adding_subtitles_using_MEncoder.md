---
title: "Adding subtitles using MEncoder"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by h4m574h on 2006-11-15
Hello once again.

I was searching for a solution to "hard-sub" my subtitles to an avi file. I found a great solution in MEncoder and the code which I found on the net to merge the subtitles with the avi:

*mencoder -vop pp=de,scale=548:222 -oac copy -ovc lavc -lavcopts keyint=25:vcodec=mpeg4:vbitrate=679:vpass=1 -sub "Domino.srt" -o "Domino_with_subs.avi" "Domino.avi"*

But the thing is, my .srt subs are in Central-European charset (ISO-8859-2), but MEncoder replaces CE-specific characters into strange symbols. Is there any way to fix this or am I forced to find another solution?

---

### Post by h4m574h on 2006-11-16
In case you are having the same problem: haven't found a way to enable ISO 8859-2, so I used another method:

I downloaded Avidemux and used the Subtitler filter found in Video>Filters. Works like a charm now.

Hope the 2 ruined days of my life will help you. =D

---

### Post by deep.tinker77 on 2006-11-28
> **h4m574h said:**
> In case you are having the same problem: haven't found a way to enable ISO 8859-2, so I used another method:

I downloaded Avidemux and used the Subtitler filter found in Video>Filters. Works like a charm now.

Hope the 2 ruined days of my life will help you. =D

It helped me, thanks for going thru the pain :D

---


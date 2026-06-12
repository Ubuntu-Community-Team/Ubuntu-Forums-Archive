---
title: "what is the best Linux video deinterlacer?"
date: 2008-07-20
forum: Art &amp; Design
---

### Post by hessiess on 2008-07-20
I have a HDV video camera that records in 1080i,which obviously needs deinterlacing for display/ editing on a computer. I have tried using cinelerra(most options) and ffmpeg with the -deinterlace switch. the output of which looks worse than displaying directionally from the camera to a HDTV.

what is the best deinterlacer for Linux?, It dose not have to be real time, but prefarabley able to work with lossless formats like PNG or EXR sequences, which is what I re-encode the MPEG2 streem into to make editing easier, and prevent loosing any more information from the alredy very lossy source material.

---

### Post by hessiess on 2008-08-07
so there isnt one?

---

### Post by timcredible on 2008-08-07
i find it hard to believe that ffmpeg doesn't do what you need.  maybe try winff as a front end gui for ffmpeg?  as for other editors, there's lives, kdenlive, kino, and you already know about cinelarra.  those are the ones i know of.

---

### Post by timcredible on 2008-08-07
oh, as for the quality in ffmpeg, use the -sameq parameter to get the same quality out as you put in.

---

### Post by miraazja on 2010-03-31
Maybe not the best, but one who works is  [SIZE=3]WinFF[/SIZE]. 
Simply install in download center and You can convert some file formats. 
Usefull.

Before converting, check additional options for deinterlace

---


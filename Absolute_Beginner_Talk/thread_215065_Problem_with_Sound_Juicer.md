---
title: "Problem with Sound Juicer"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by LordofHaha on 2006-07-13
I was able to install Lame and in theory rip to MP3's with a variable bit rate around 192. But when I tried ripping a CD (Speakerboxxx / Love Below to be exact) I found that all my mp3's were coming out 25-400% longer then they should be. For example the 1st song on the 2nd disk (The Love Below) should be 1:27 but when I ripped it, I managed to create a 9:13 song, same goes with the rest of the songs with from about 30 to nearly 8 minutes! extra added to them.

So my question is what am I doing wrong? Or is there a better program I can use to rip to mp3 with... 

My currently pipeline is: 
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! id3v2mux
```

---

### Post by T700 on 2006-07-13
That's a real puzzle!  When you play the stretched track, what is filling up the extra time?  Does the song repeat?

Paul

---

### Post by Mike_N on 2006-07-13
I've tried several CD rippers and i've found Goobox to be my favorite thus far...

---

### Post by LordofHaha on 2006-07-13
starts to repeat mostly... and I will try that ripper out later...

---

### Post by LordofHaha on 2006-07-14
Got around my issues by using KAudioCreator if anyone is curious.

---

### Post by T700 on 2006-07-15
Thanks for posting back with a solution!

Paul

---


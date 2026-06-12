---
title: "Sound Juicer - can I make it rip faster"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-01-24
When I use Sound Juicer, it's ripping at a rate of between 1.2x and 1.4x (for mp3s at 192Hz).  This is...errr...disappointing.

Is there any way to make it go faster?  My CD drive is obviously capable, and my Windoze apps can do it, but I can't see anything obvious in its settings.  

Is it anything to do with the rate variable in this line [COLOR="Blue"][COLOR="Sienna"]audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128[/COLOR][/COLOR] (Gstreamer pipeline settings in my mp3 profile, taken from the wiki)

Alternately...is there a faster ripper out there?

---

### Post by ned.b on 2006-01-24
Try this:

[https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

---

### Post by Edward The Bonobo on 2006-01-25
Thanks.  

However: 'DMA is normally available in machines less than four years old.'

My machine is eight - yes, eight - years old.  (At least the big bits.  Some newer components).  What are the risks?

---


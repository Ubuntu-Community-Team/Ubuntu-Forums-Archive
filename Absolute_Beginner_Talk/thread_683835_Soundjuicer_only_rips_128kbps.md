---
title: "Soundjuicer only rips 128kbps"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by mexicola on 2008-01-31
I've been searching the web for quite some time, and found nothing.

Sound Juicer 2.20.1

Gstreamer pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

From what I've read, this should make ~192kbps mp3's, right? Still the file info says 128kbps. What's the problem?


Thanks.

---

### Post by emarkd on 2008-01-31
You're encoding those mp3's using VBR - variable bit rate. To say what the bitrate is makes no sense because it varies throughout the file.  For a more useful bit of math, try calculating the average bitrate. Take the filesize and devide it by the duration.  For instance, assume a 5MB file that lasts 3 minutes:

5242880 * 8 / 180 / 1000 = ~233 kbps

---

### Post by mexicola on 2008-01-31
Oh, of course, thanks! But, shouldn't the file info bitrate still be higher? I don't think any of my other, uhm, not self-ripped mp3 vbr's reads as 128kbps. The quality is fine though, it just bothers me that it reads as 128 kbps...

---

### Post by emarkd on 2008-01-31
I don't know why it reads that way.  The file doesn't even really have a bitrate.  Sound Juicer or lame may be just putting a default value in the header field.  I don't know...

---

### Post by mexicola on 2008-01-31
Ok, thanks.

---

### Post by stchman on 2008-01-31
> **mexicola said:**
> I've been searching the web for quite some time, and found nothing.

Sound Juicer 2.20.1

Gstreamer pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

From what I've read, this should make ~192kbps mp3's, right? Still the file info says 128kbps. What's the problem?


Thanks.

I have a tutorial for rippind CDs to MP3s.  It includes getting SJ to rip VBR and 192.  You can adjust the bitrate as desired.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---


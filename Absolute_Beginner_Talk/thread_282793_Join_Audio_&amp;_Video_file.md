---
title: "Join Audio &amp; Video file"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Bajo_sk on 2006-10-23
Hi..

I have a problem ](*,) 
I have separate audio and video file. Audio is standard wav file, video is m2v file (grabbed on omneon broadcast system). How can I join these files to single video (maybe mpeg or avi) file or how can I make dvd from these files .)

---

### Post by Ben Sprinkle on 2006-10-23
Find a video editing program via google or something, add the wav into the video.
Simple. :)

---

### Post by Bajo_sk on 2006-10-23
hm, on windows it's no problem ... but on ubuntu ... :(

---

### Post by xyz on 2006-10-23
No expert at all here but:
>     *  The video stream is compressed to make the DVD fit on 4.7 Gb recordable DVD
    * DVD Burning
    * Creation of ISO images
    *** Possibility of selecting the audio tracks and subtitles to be copied**
    * Title preview (video only)
    * Possibility of preserving the original menus

[K9Copy]("http://k9copy.sourceforge.net/index.php")

Let me know...I'd be interested in finding about about this.
Thx.

---

### Post by Bachstelze on 2006-10-23
Avidemux will do it. I'm not 100% sure whether it supports m2v input though.

---

### Post by xyz on 2006-10-23
> **HymnToLife said:**
> Avidemux will do it. I'm not 100% sure whether it supports m2v input though.
You may just be quite right but I' not sure I understand this right:
> With avidemux you can open divx, process the audio track with the included
filters and save a part of the avi (i.e. split).

**De-multiplex audio & video is also possible**, the audio track can be coming
from the avi or an external Wav/MP3 file.
Is the **bold** line what we are looking for here?

---

### Post by Bachstelze on 2006-10-23
Yep :)

---

### Post by xyz on 2006-10-23
> **HymnToLife said:**
> Yep :)
Great...thanks!

---

### Post by Bajo_sk on 2006-10-23
k9copy is the same as dvdshrink...it is capable to separate audio trace, but is unable to add it 
avidemux encounters an error while adding audio file, I will try to use another format
Thank you very much for your help so far :)
 
edited:
heh .. sorry .. my english is terrible .. 

here is video/audio test files .. 
[http://www.bajo.sk/audiovideo.zip](http://www.bajo.sk/audiovideo.zip)
(size is 60Mb)

---

### Post by xyz on 2006-10-23
> **Bajo_sk said:**
> k9copy is no way for me. 
 
avidemux still allways ignore me
here is video/audio test files .. 
[http://www.bajo.sk/audiovideo.zip](http://www.bajo.sk/audiovideo.zip)
(size is 60Mb)
What do you mean "avidemux still allways ignore me?"

---

### Post by Bajo_sk on 2006-10-23
> **xyz said:**
> What do you mean "avidemux still allways ignore me?"

avidemus encounters the same error "could not open the file" whether adding audio file as wav format or mp3 format... it just ignores me

---

### Post by xyz on 2006-10-23
Like I said, I'm no expert but these seem to be supported in Avidemux! Is your "m2v" in there?

> Supported Input Formats

File formats:

    * AVI, OpenDML
    * MPEG
    * NuppelVideo
    * Images (BMP, JPEG, PNG)
    * OGM
    * QuickTime, MP4, 3GPP 

Video codecs:

    * DV
    * FFV1
    * H.263
    * H.264
    * HuffYUV
    * MPEG-1, MPEG-2
    * MPEG-4 Simple Profile/Advanced Simple Profile (Supported FourCCs: DIVX, DX50, XVID, FMP4, M4S2)
    * MJPEG
    * MSMPEG-4 v. 2 (FourCC DIV3)
    * Raw RGB
    * SVQ3
    * VP3
    * WMV 2 

---

### Post by Aditz on 2006-10-23
Try [mkvtoolnix]("http://www.bunkus.org/videotools/mkvtoolnix/downloads.html").

---

### Post by Bajo_sk on 2006-10-23
Dear Aditz, 
your suggestion was great. This software runs perfectly. It is exactly what I was looking for and what I needed.
Lots of thanks to all of you, especially Aditz.

---


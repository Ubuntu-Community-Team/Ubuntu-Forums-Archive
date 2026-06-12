---
title: "AIFF file convertion"
date: 2008-02-25
forum: Apple PPC Users
---

### Post by mrowl on 2008-02-25
My brother has been sending me files in the AIFF format of my grandmother's and great-aunt's old LP's he has digitized. Although Adacious can play them, Serpentine does not recognise them. Any suggestions of how I can record these files to a CD.

---

### Post by yabbadabbadont on 2008-02-26
You might try using sox to convert them into wav files.  You might also be able to do so using ffmpeg, if you already have it installed.

---

### Post by 3rdalbum on 2008-02-27
You can open them in Audacity, and then go to File > Export... and export them as WAV, which Serpentine can deal with.

Or you can use the Sox command-line tool to convert them.

```
sox track1.aiff track1.wav
```

Substituting "track1.aiff" for the actual filename of the file, of course.

The third option is that I can package up my old GUI program "Aiff Interchange" and send you the .deb, but it just tells Sox to do the dirty work anyway.

---

### Post by mrowl on 2008-02-29
Thank you  for suggestions

I've tried sox but it returned the following:

"sox stio: Failed reading `track01.aiff': AIFC files that contain compressed data are not supported: ima4"

and Audacity opens them as a blank track

---

### Post by oswaldkelso on 2008-03-03
if its a one off you can use an online converter I used this link to convert a phone video when I failed to find a linux tool

[http://media-convert.com/](http://media-convert.com/)

---

### Post by 3rdalbum on 2008-03-03
Ouch... your brother has applied IMA 4:1 compression to the files. This severely impacts on quality, and makes it non-cross-platform.

Do you want to ask him to send the originals, or (if he recorded straight into the compressed format) re-digitise the records again? He could probably convert to MP3 from his end if quality isn't too important, and realistically MP3 is smaller and better quality than IMA.

---

### Post by mrowl on 2008-03-03
Thanks for the info;

No there are a lot of files - there were several collectors in my family 78's and LP's so the on-line suggestion is not practical. Especially on rural dial-up.

I'll see if I can get him to redo them as mp3

---


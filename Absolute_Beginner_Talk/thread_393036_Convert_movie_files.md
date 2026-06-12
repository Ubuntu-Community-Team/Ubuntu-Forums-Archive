---
title: "Convert movie files"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by ppsieradzki on 2007-03-25
Im running edgy. I have all the codecs installed. I want to put an avi movie (its an entire DVD) onto my cell phone. All i need is a converter that can convert between AVi and 3GPP2 (that is the cell phone video type)

Anybody know an easy to use converter that works well?

ThANK YOU IN ADVANCE!

---

### Post by zvacet on 2007-03-26
[http://doc.gwos.org/index.php/Nautilus_Video_Converter]("http://doc.gwos.org/index.php/Nautilus_Video_Converter")

---

### Post by mimsmall on 2007-03-26
I use FFmpeg to work with .3gp files I generate on my Nokia celtel.

---

### Post by jakev383 on 2007-04-14
> **ppsieradzki said:**
> Im running edgy. I have all the codecs installed. I want to put an avi movie (its an entire DVD) onto my cell phone. All i need is a converter that can convert between AVi and 3GPP2 (that is the cell phone video type)

Anybody know an easy to use converter that works well?

ThANK YOU IN ADVANCE!

Follow this guide:
[http://blogger.rukker.org/2007/01/29/enable-mp3-and-amr-support-in-ffmpeg-ubuntu-edgy-eft/](http://blogger.rukker.org/2007/01/29/enable-mp3-and-amr-support-in-ffmpeg-ubuntu-edgy-eft/)

And the run this command:
```

ffmpeg -i video_file.avi -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y video_file.3gp

```

---


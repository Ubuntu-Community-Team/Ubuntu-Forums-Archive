---
title: "Record sound from my sound card"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-06-03
Ok, this is what I want to do...
I've got a flash with sound I want to get. But I don't know how. So the only idea that came to my mind is to somewhat rip it, or record it from sound card. But that's also what I don't know how to do?
any ideas would be welcome

---

### Post by Ek0nomik on 2007-06-03
Yeah, more specifically you want a Line-In recorder.

I know of such programs for Windows, but I don't for Linux.  Audacity is a music editing program, and it might allow you to do it.  I am looking into it right now.  I will search around and post something if I can find something as well.

---

### Post by Ek0nomik on 2007-06-03
**Audacity** will do it.

I just loaded Audacity, hit the red circle to record, and it automatically records from Line-In by default.

```
sudo apt-get install audacity
```

---

### Post by ltk5 on 2007-06-03
ok i checked audacity. but as it seems, I don't have the mixer toolbar. I tried recording but no sound got recorded - now i know i want to record the line out.
i also checked the forums and found this [http://audacityteam.org/wiki/index.php?title=Mixer_Toolbar_Issues#Linux-specific_issues](http://audacityteam.org/wiki/index.php?title=Mixer_Toolbar_Issues#Linux-specific_issues)
might be my problem.. 

still thx for your help

---

### Post by annda on 2007-06-03
do you want to extract audio from a flash video file? if so, you can use the workaround with ffmpeg and avidemux (i know it can probably be done with ffmpeg alone, but i'm not so smart...)

```
ffmpeg -i flash_filename.flv -acodec mp3 -ab 128 -ac 2 output_filename.avi
```

then in avidemux open the avi file and select 'save' from the audio menu.

---

### Post by ltk5 on 2007-06-04
perfect!
that was it, thx

---

### Post by nphx on 2007-06-22
or you can simiply:

```
ffmpeg -i FlashFileName.flv -f mp3 -vn -acodec copy AudioFileName.mp3
```

for OGG vorbis:

```
ffmpeg -i FlashFileName.flv -f ogg -vn -acodec vorbis AudioFilename.ogg
```

---


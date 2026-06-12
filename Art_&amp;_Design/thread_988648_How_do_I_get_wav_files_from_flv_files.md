---
title: "How do I get wav files from flv files"
date: 2008-11-20
forum: Art &amp; Design
---

### Post by TheForkOfJustice on 2008-11-20
I use **clive** to nab flv files direct from youtube and convert them to avi files (I could also convert them to mpeg).

Next, I used **avidemux** to edit the video files to the sections containing the audio I want.

The last part is what I have trouble with: _How to I save just the audio from the video file as a wav?_

---

### Post by SuperSonic4 on 2008-11-20
Do you need them to be wav? I have a working script for mp3 but doesn't seem to like wav. Copy and paste the below into your favourite text editor and save it (I'm using converter as an example). Replace dwhelper with the directory that the flv file is in.

```
#!/bin/bash
cd ~/dwhelper
for i in *.flv; do ffmpeg -i "$i" -acodec copy "`echo "$i" | sed -r -e 's/(.*)\.flv$/\1.mp3/'`"; done
```

In terminal
```
chmod +x ~/converter
```
to run:```
./converter
```

You could get away with changing mp3 to wav but it didn't work for me

---

### Post by TheForkOfJustice on 2008-11-20
That script worked perfectly.  I'll fiddle with the mp3>wav conversion tomorrow.  The result was actually better than the conversion that clive did for me.

EDIT

Since I suck at bash can you explain to me exactly what is happening in your script here:

```
for i in *.flv; do ffmpeg -i "$i" -acodec copy "`echo "$i" | sed -r -e 's/(.*)\.flv$/\1.mp3/'`"; done
```

---

### Post by FakeOutdoorsman on 2008-11-21
You could just run ffmpeg itself.  To copy the mp3 stream from a flv file:
```
ffmpeg -i inputfile.flv -acodec copy output.mp3
```
To transcode the audio in the flv to wav:
```
ffmpeg -i inputfile.flv output.wav
```

---

### Post by eightmillion on 2008-11-21
A lot of people don't realize that you can do substitutions with bash. The pipe to sed is  unnecessary.

This:
> for i in *.flv; do ffmpeg -i "$i" -acodec copy "`echo "$i" | sed -r -e 's/(.*)\.flv$/\1.mp3/'`"; done

Could be done with this:
> for i in *.flv; do ffmpeg -i "$i" -acodec copy "${i/.flv/.mp3}"; done

---


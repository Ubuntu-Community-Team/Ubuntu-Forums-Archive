---
title: "Audio Converter"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by StopTheOncoming on 2007-10-22
I have downloaded SoundConverter in hopes of converter some AAC(mp4) files into MP3 files. But when I open them and tell SoundConverter to convert then, it just says "file xxx of yyy (333 minutes remaining)". I've let it sit for a good while hoping it would start up with no luck.

So could anyone point me towards an AAC (mp4) to MP3 converter?

Thanks!

---

### Post by Microsoft_Sam on 2007-10-22
nautilus-script-audio-convert
Make sure you install faac and lame for aac and mp3 support.
Open a terminal and enter the command:
```
nautilus-script-manager enable ConvertAudioFile
```

Then open up nautilus and right-click your aac files, go to scripts>ConvertAudioFile and select mp3

---

### Post by StopTheOncoming on 2007-10-22
Thanks, worked like a charm.

---


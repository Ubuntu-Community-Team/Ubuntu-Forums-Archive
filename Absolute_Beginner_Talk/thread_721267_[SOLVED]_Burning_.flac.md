---
title: "[SOLVED] Burning .flac"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2008-03-11
If I burn .flac files onto a CD will I be producing an exact copy of the CD I originally created the .flac files from?

---

### Post by jken146 on 2008-03-11
Not if you just burn the files to a CD.  That would be a data CD, just like getting a load of images and burning them to a CD.

You should use something like GnomeBaker, Brasero or K3B to burn an audio CD.


I'm not sure if the audio quality will be the same as the original CD.  You'd think so, wouldn't you?

---

### Post by scragar on 2008-03-11
odd's are it will not be an exact duplicate, but flac is loss-less in terms of quality, so I can't see any problems(except maybe music titles or some such).

you can use dd to backup a CD perfectly to an iso and burn this iso as an exact duplicate:
```
dd if=/dev/**CDdevice** of=**pathToSaveIso,Including.isoPart**
```

---


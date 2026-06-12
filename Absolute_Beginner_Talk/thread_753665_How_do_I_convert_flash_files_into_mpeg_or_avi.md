---
title: "How do I convert flash files into mpeg or avi?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2008-04-12
I have flash files from you tube (.flv). I want to convert those to mpeg or avi files. what software should i use? i am using kubuntu gutsy as my os.

---

### Post by Mark20 on 2008-04-13
```
ffmpeg -i yourfile.flv -ar 48000 -ac 2 newFile.avi
```

Alternatively you could buy software that does a better job.  But I'm sure there's a better (free) way to do it as well.

---


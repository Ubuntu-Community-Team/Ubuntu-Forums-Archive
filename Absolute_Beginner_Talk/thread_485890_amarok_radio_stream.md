---
title: "amarok radio stream"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ktown on 2007-06-27
hey whenever i use amarok and attempt to play a radio stream an error message comes up saying
"no suitable demux plugin"

any suggestions?

---

### Post by Jellyffs on 2007-06-27
Hi,

I think you need this package:

```
libxine-extracodecs
```

You need it for mp3 playback, but also for radio if I remember well.

---

### Post by Jellyffs on 2007-06-27
that might help too:

[https://answers.launchpad.net/ubuntu/+source/amarok/+question/6446](https://answers.launchpad.net/ubuntu/+source/amarok/+question/6446)

---

### Post by Boris-- on 2007-06-27
i have a similar problem, mine won't play mp3s. I need xine mp3 codec then, too? and wma?

---

### Post by Jellyffs on 2007-06-27
> **Boris-- said:**
> i have a similar problem, mine won't play mp3s. I need xine mp3 codec then, too? and wma?

Absolutly. For wma, you "might" need "w32codecs" package too.

---

### Post by orange2k on 2007-06-27
I installed every package needed by Amarok using Automatix2. I know its not officially supported, but it was quite easy and fast...
I installed every single codec that is available, so now I don`t have any problems with mpg, wma, divx, xvid, etc. you name it...
I wouldnt recommend it, but it works...:)

---

### Post by bigken on 2007-07-02
sudo aptitude install libxine-extracodecs  

sudo aptitude install w32codecs

---


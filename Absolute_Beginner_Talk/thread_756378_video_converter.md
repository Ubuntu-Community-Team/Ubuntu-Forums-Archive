---
title: "video converter"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-04-15
is there a video converter included with Ubuntu 7.10 that can convert avi to mpeg and visa versa?  if not, what is the best one to use for this task?  thanks.

---

### Post by Crafty Kisses on 2008-04-15
> **Matt26 said:**
> is there a video converter included with Ubuntu 7.10 that can convert avi to mpeg and visa versa?  if not, what is the best one to use for this task?  thanks.

Yeah, you might want to try Mencoder.

```
sudo apt-get install mencoder
```

---

### Post by spiderbatdad on 2008-04-15
also, ffmpeg works well...a little easier to use than mencoder...imo.

---

### Post by Inxsible on 2008-04-15
> **spiderbatdad said:**
> also, ffmpeg works well...a little easier to use than mencoder...imo.
+ 1 for ffmpeg

---

### Post by jbrown96 on 2008-04-15
If you only want to convert video, I would use MEncoder. Install it with```
sudo apt-get install mencoder
```
It's a command line tool but very easy to use. However, the choice of video/audio codecs is daunting, especially the whole container/format thingy. Here's a gentoo guide [http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide")that should help. Hopefully, the codecs aren't confusing but the tool is very easy.

The problem with FFmpeg AFAIK is that it won't do mpeg to avi.

---

### Post by sdowney717 on 2008-04-15
Convertit

[http://www.sciallo.net/ConvertIT](http://www.sciallo.net/ConvertIT)

[http://ubuntuforums.org/showthread.php?t=683584&highlight=Convertit](http://ubuntuforums.org/showthread.php?t=683584&highlight=Convertit)

---

### Post by spiderbatdad on 2008-04-15
> The problem with FFmpeg AFAIK is that it won't do mpeg to avi.

Of course it will, and losslessly.
```
ffmpeg -i "input-file.mpg" -acodec copy -vcodec copy "output-file.avi"
```

---


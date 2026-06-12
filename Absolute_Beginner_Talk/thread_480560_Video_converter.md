---
title: "Video converter"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by luckyd on 2007-06-21
Are there any all purpose gui video converters for ubuntu like ffmpegx for os x?

---

### Post by jfinkels on 2007-06-22
> **luckyd said:**
> Are there any all purpose gui video converters for ubuntu like ffmpegx for os x?

You can try avidemux, it's really a video editing program, but you might try it (i have no idea, never used it):```
sudo aptitude install avidemux
```

You don't really need a GUI, though, for simple transcoding. You just need mencoder:```
sudo aptitude install mencoder
```

Unfortunately I don't know the syntax for using mencoder, either. Search around the forums, though.

---


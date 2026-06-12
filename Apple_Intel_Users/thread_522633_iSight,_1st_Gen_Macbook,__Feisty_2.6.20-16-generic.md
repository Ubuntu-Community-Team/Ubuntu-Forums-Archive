---
title: "iSight, 1st Gen Macbook,  Feisty 2.6.20-16-generic #2 SMP issues..."
date: 2007-08-10
forum: Apple Intel Users
---

### Post by poncenby on 2007-08-10
Followed the "New Quick Install" found in the first post here [http://ubuntuforums.org/showthread.php?t=225621](http://ubuntuforums.org/showthread.php?t=225621)

However this command...
```

gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink

```

errors with...

```

Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device "/dev/video0".
Additional debug info:
v4l2_calls.c(404): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...

```

any idea of ways to get iSight working or what file/directory the above command is looking for...

thanks in advance

---


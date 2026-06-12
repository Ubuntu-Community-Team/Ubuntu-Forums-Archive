---
title: "How do I know if I have v4l2?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-13
I've been messing around with this site:
[http://www.linuxtv.org/v4lwiki/index.php/Gstreamer](http://www.linuxtv.org/v4lwiki/index.php/Gstreamer)

But I can't get the example to work...

```

thuskins@thuskins-desktop:~$ uname -r
2.6.22-14-generic

```

```

thuskins@thuskins-desktop:~$ gst-launch-0.10 v4l2src use-fixed-fps=false ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=320,height=240 ! ffmpegcolorspace ! ximagesink

(gst-launch-0.10:26776): GStreamer-WARNING **: Failed to load plugin '/usr/local/lib/gstreamer-0.10/libgstapp.so': libgstapp-0.10.so.0: cannot open shared object file: No such file or directory
ERROR: pipeline could not be constructed: no element "v4l2src".
thuskins@thuskins-desktop:~$ 

```

But I thought v4l2 was in the kernel or something?

What should I do to find out if it's installed?

---

### Post by joesmith1234 on 2008-02-13
bump-a-dump

---

### Post by Golem XIV on 2008-02-13
Run gstreamer-properties and check under the Video tab, Default Input

---


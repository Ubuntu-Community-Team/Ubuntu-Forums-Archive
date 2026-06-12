---
title: "Istanbul Debug. Please Help"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2008-03-26
I want to record a screencast with sound with Istanbul. I get this error
```
DEBUG: final pipeline: oggmux name=mux ! filesink location=/tmp/tmpV_fxzK istximagesrc name=videosource display-name=:0.0 screen-num=0 ! video/x-raw-rgb,framerate=10/1 ! videorate ! ffmpegcolorspace ! videoscale method=1 ! video/x-raw-yuv,width=1280,height=800,framerate=10/1 ! theoraenc ! queue ! mux. gconfaudiosrc name=audiosource ! audioconvert ! vorbisenc ! queue ! mux.

```

What do I have to do to fix it?

Better yet, how can I record a screencast with VLC? What would I have to set as my video device name?

---

### Post by DBrocks on 2008-03-28
[http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/](http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/)

This is a full tutorial on how to record a screencast.

---


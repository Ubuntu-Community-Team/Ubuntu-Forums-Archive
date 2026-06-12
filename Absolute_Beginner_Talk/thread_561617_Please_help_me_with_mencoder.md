---
title: "Please help me with mencoder"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-09-27
I need these exact settings

```
Upload Format: Flash FLV
Resolution: 450 x 337
Frame Rate: 30 FPS
Key Frame Every: 45 Frames
Video Data Rate: 2000 Kbps
Audio Data Rate: 128 Kbps
Total Data Rate: 2125 Kbps
Sorenson 2-Pass VBR
Total File Size: 15914 KB
```

Here's what I usually use
```
mencoder /home/tyler/gibson_station_9_10_07.avi -o outputfilename1.flv -of lavf -oac mp3lame -lameopts br=128 -af lavcresample=22050 -srate 22050 -ovc lavc -lavcopts vcodec=flv:vbitrate=300:autoaspect:mbd=2:trell:v4mv -vf scale=450:337 -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames 


```

but I need to adapt it to those settings. Any ideas?

---

### Post by tdrusk on 2007-09-29
bump

---


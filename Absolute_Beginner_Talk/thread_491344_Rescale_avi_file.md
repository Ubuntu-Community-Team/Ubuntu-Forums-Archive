---
title: "Rescale avi file"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by KriZo on 2007-07-03
Hi i just bought a nice mp4 player and i should be able to play avi files, but i have to rescale them to 320*240, i know i have to rescale it using mencoder, i used this command to rescale my movie:

mencoder input.mpg -ovc lavc -lavcopts vcodec=mpeg4 -vop scale=320:240 -oac copy -o output.avi

But it wont work, my mp4 player tells me that it's the wrong format. In my mp4 player specifications list it says: "Plays AVI video files DviX/Xvid 320x240". Is there any thing else I need to type in my command to get the right format?

---

### Post by benanzo on 2007-07-03
I'm not sure exactly of the configs required in mencoder.  If you don't mind giving up scriptability, you can use **avidemux** to convert your videos for use on mpeg4-compatible players.

```
sudo apt-get install avidemux
```

It will do XviD, DivX, H.264 (x264), OGG etc with ease.

---


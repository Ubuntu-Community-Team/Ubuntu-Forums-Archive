---
title: "isight with vlc?"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by themoebius on 2008-03-24
I'm trying to display my isight using VLC. I have the camera working with skype, but when I start vlc using video device /dev/video0 it gets no video. I also tried plugging in an external firewire camera which shows up at /dev/video1394/0 and I tested it successfully with coriander, but it also doesn't open with vlc. Is there anything special that needs to be done?

zac@zac-laptop:~$ vlc v4l:// :v4l-vdev="/dev/video1394/0" :v4l-norm=3 :v4l-frequency=-1
VLC media player 0.8.6c Janus
[00000293] v4l demuxer error: cannot get capabilities (Inappropriate ioctl for device)

zac@zac-laptop:~$ vlc v4l:// :v4l-vdev="/dev/video0" :v4l-norm=3 :v4l-frequency=-1
VLC media player 0.8.6c Janus
[00000293] v4l demuxer error: cannot get channel infos (Invalid argument)

Using macbook pro and 7.10

Thanks.

---

### Post by benanzo on 2008-03-25
I believe VLC doesn't handle v4l2 devices currently, only v4l.  Since the iSight is built for v4l2 I don't think it will work.

---


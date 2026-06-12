---
title: "Want to use Creative web cam with Linux video editiing software"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by roidfits on 2007-05-20
I want to be able to use a creative web cam that will capture video. I want to edit the video with some video editing software. Is there any software that can capture from a web cam? I would really appreciate it. In other words, I am looking for software that is comparable to Windows movie maker, in which I can capture video from the web cam and edit the video with the same program.

---

### Post by helgi on 2007-05-20
Well I have I creative web cam as well. So it would be great if somebody could give some advise.
Thanx

---

### Post by jiminycricket on 2007-05-21
Check if your web cam is supported here at mxhaard's site: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Some video editing programs might support this.  Maybe Pitivi, LiVeS, kdenlive.  I know Kino only supports DV capture.  Diva is still in heavy development.

If nothing comes up, you can capture the video camera output from /dev/video0 with mplayer, then edit the resulting .avi file with one of those programs.  [http://gentoo-wiki.com/HOWTO_Install_a_webcam#Testing_your_camera](http://gentoo-wiki.com/HOWTO_Install_a_webcam#Testing_your_camera)

---


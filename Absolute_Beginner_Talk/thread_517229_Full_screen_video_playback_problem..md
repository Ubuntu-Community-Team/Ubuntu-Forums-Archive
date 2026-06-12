---
title: "Full screen video playback problem."
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by linux123 on 2007-08-04
I'm using ATI Radeon X200 graphic card. I have already installed the ATI driver for my vga card. But when i play a video in full screen mood, videos are playing but skipping. It seems something wrong in video rendering. But when i play videos in a small window, it plays smooth and continuously. But as i resize the window to higher, the skipping effect gets greater. how can i overcome this problem? 

Channa.

---

### Post by benx009 on 2007-08-04
yes, i would think this would be a video problem.  as you may already know, the ati drivers are very hard to set up in linux; even when they are set up, they are still very buggy.  do you get a decent fps when you run "glxgears" in a terminal?

---

### Post by linux123 on 2007-08-04
Yeh! It Seems good!
Anyway, I Think I Installed **ATI Drivers** Correctly, And I'm Using **Compiz **too!
 I'm Using **1280*1024** Screen Resolution. So Do you think is that will caused for Video Playback??
Is there are any way to change quality or some thing in video playback given by **ATI**?
I mean Full screen Video Playback Resolution or Some thing??

Thanks.
**Channa**

---

### Post by khughitt on 2007-08-04
Heya,

A couple of things you could try to narrow down the range of possible problems:

1. Try playing the video in full-screen at a slightly smaller resolution (e.g. 1024x768).
2. Try logging into **Gnome** instead of **Xgl**

If the problem still remains in both those cases, you can try temporarily disabling the composite extension and logging into gnome. First though, can you post the contents of your **/etc/X11/xorg.conf** file here?

---


---
title: "vlc video problem"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-10-13
I installed vlc media player through synaptic and it plays all sorts of movies without the video. The sound comes perfectly but there is just a blank black screen instead for the video. Please help me... Thanks in advance...

---

### Post by alienexplorers on 2007-10-13
Do you have all the correct codecs installed?

---

### Post by Rabindranath on 2007-10-13
Yes, I think so. Wont synaptic install all the required codecs?

---

### Post by FuturePilot on 2007-10-13
Try running that really long command about halfway down this page
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Rabindranath on 2007-10-13
I tried that and it doesn't work. The video appeared for about a fraction of a second until the vlc window appeared at the correct position from the taskbar and then the video was gone. Only black screen again.

---

### Post by Rabindranath on 2007-10-13
I just called my friend and he told me to disable the desktop effects and it worked. I dont know how enabling the desktop effects would cause a black screen in vlc. Does the desktop effects affect vlc's functioning?

---

### Post by FranMichaels on 2007-10-13
Hi, what video card do you have? I had a similar problem, but it was fixed in Gutsy (intel 945 chipset.) 

The workaround I used was changing the video ouput from xv to something else. 
 :KS

---

### Post by Campingman on 2007-10-13
Hi,

You can get around this by setting video output in the VLC player  (I have not got it installed at the moment so I cannot guide you through),  The solution is in this thread
[http://ubuntuforums.org/showthread.php?t=415012&highlight=campingman](http://ubuntuforums.org/showthread.php?t=415012&highlight=campingman)

Try this:
In VLC if you go to settings/preferences/video/output modules click advanced options you can change the video output, I have tried X11 video output and Xvideo extension video output, Both work OK

---


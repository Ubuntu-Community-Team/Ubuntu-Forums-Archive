---
title: "Resolution incorrectly detected by Ubuntu, differently detected in Knoppix, Mepis etc"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-13
Hello.. 

Starting from the server installation 3 times, I have installed xubuntu-desktop, kubuntu-desktop and ubuntu-desktop, but in all the cases I have managed to get only a 1600x1200 resolution. I would like to keep things strictly at 1024x768 only. 

In Windows, 640x480 800x600 1024x768 1280x1024 1600x1200 all works fine. Knoppix boots with a default of 1024x768 and so does Mepis. 

How do I force Ubuntu to disply at 1024x768. I tried tweaking the conf file in /etc/X11 but it only shows a garbled screen and then quits back to the terminal (after startx) and spouts error messages. 

Any help / suggestions here? 

Thanks..

---

### Post by aysiu on 2005-12-13
Maybe control-alt-F1 and ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Gustav on 2005-12-13
Or (to get the best result) [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by harisund on 2005-12-13
Well..dpkg-reconfigure xserver-xorg didn't quite work. 

However, I copied the relevant monitor configuration lines from the XF86Config file of Knoppix and pasted into Ubuntu's xorg.conf and now my monitor displays a perfect resolution of 1024x768.

Thanks !

---


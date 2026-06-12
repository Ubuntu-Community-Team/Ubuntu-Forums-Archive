---
title: "replaceing monitor"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by mamasita on 2008-03-16
my old monitor gave out it was actually a tv/monitor.  I am useing ubuntu 7.10 i386 and my new resolution for my monitor was a 1280x768 for this was the optimal resolution for my new monitor which is a hp it is 1920x1200@60hz.  So how do I configure this so that ubuntu can pick this up?  Thanks for your help in advance.
:guitar:

---

### Post by MasterJS on 2008-03-16
It may be that you need to reconfigure X.org to know how to use your new monitor. You can use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` You'll have to pass through a set of choices like choosing the video driver, the monitor resolution, and such things. [HTML]http://www.youtube.com/watch?v=2QsP8GDTpno[/HTML] Here's a youtube video that shows the general gist of what you would have to do. Also, if your video card is Nvidia as it shows in the video, when your at the driver list, search for "ati".

---


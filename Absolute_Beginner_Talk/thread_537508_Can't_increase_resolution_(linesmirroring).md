---
title: "Can't increase resolution (lines/mirroring)"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Singee15 on 2007-08-29
I have a new install of feisty - I can't increase the screen resolution. Any resolution other than 1024x768 get all messed up! (see link)

[http://picasaweb.google.com/Singee15/Temp/photo#5103980735165712386]("http://picasaweb.google.com/Singee15/Temp/photo#5103980735165712386")

I have no clue what to do, I have a Radeon Mobility 9600 on at Dell Inspiron 8600.

Thanks in advance!
~Mike

---

### Post by splintercellguy on 2007-08-29
Have you tried doing sudo dpkg-reconfigure xserver-xorg?

---

### Post by Singee15 on 2007-08-29
Yes, didn't help. Then again I wasn't exactly sure what options I should be changing.

---

### Post by Singee15 on 2007-08-29
Is it a driver issue or something similar? I have never had any problems with previous versions of Ubuntu on this computer, all ideas appreciated! Thanks.

---

### Post by beyboo on 2007-08-29
I ran 7.0.4 for the first time today and found the same resolution problem. my Viewsonic E70f old monitor dint go beyond 640x480.

Ran the  sudo dpkg-reconfigure xserver-xorg command and reconfigured the server. 

I specifically tagged the higher resolutions in the configuration and it saved the conf file. After that the higher resolutions do come, however they are messed up. Mirrored like you say. In fact I notice that the movie player also crashes when it tries to load any avi or divx file. 

I suspect, its to do with the xorg.conf file which has wrong values for the frequency of the monitor.

If you got Windoze :( - try checking the frequency at which the higher resoultions work and mimic them in the xorg.conf file. This should take care. 

I have a Intel 915GLVG motherboard with i915 display chipset. The driver X-server  takes is the i810.  

I am gonna do some work on this tonight. Will let you know what I get :)

PS. Take a look at this [http://ubuntuforums.org/showthread.php?t=405894](http://ubuntuforums.org/showthread.php?t=405894)

---


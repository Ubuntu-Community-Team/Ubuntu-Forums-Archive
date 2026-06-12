---
title: "Setting refresh rates"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by kel on 2005-09-15
Hi all, I've installed the nvidia-glx drivers through synaptic but when I go to system/preferences/Screen resolution the options for setting up my resolutions/refresh rates are still the same as they where before. I guessed that installing the drivers may have gave me more options here?

The driver are working though, as i get the nvidia splash at startup and the opengl screen savers work a hell of a lot better.

So, how do i go about setting up my refresh rates to somthing more comfortable, the resolution options are fine but i can old pick a 60Hz refresh for each option and its starting to give me a head ache :D

thanks

---

### Post by frodon on 2005-09-15
You need to add hsync and vertsync parameters of your monitor in the /etc/X11/xorg.conf file and then restart xserver.
I give a link to one of the numerous threads about that : [http://ubuntuforums.org/showthread.php?t=64137&highlight=refresh+rate](http://ubuntuforums.org/showthread.php?t=64137&highlight=refresh+rate) just be careful to put the exact parameters (see your screen specification).
To get more threads about that use the search field of the forum with refresh rate or screen resolution as keyword.

good luck  ;-)

---

### Post by kel on 2005-09-15
Thanks for the link frodon. I'd done a quick search but guessed i might have been missing something really obvious, or there may of have been a more tidy solution.

Cheers.

---

### Post by frodon on 2005-09-15
If you still have problems give the more details you can and post your xorg.conf file : ```
sudo gedit /etc/X11/xorg.conf
```

---


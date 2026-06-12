---
title: "m1210 resolution"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Nxion on 2008-02-21
Hi,

I have a m1201 XPS laptop. Everything is working fine on it. The only issue I have is the screen resolution when you boot up. Its huge. How can I make it 1280x800 ?

I have tried this guide with no luck:
[http://ubuntuforums.org/showthread.php?t=492487](http://ubuntuforums.org/showthread.php?t=492487)

It always tells me "Video mode not defined" or something to that affect.

Any help would be greatly appreciated !

---

### Post by S15_88 on 2008-02-21
from the terminal: 
sudo dpkg-reconfigure xserver-xorg

or try 

sudo gedit /etc/X11/xorg.conf 

and change the resolution there

Thanks, Alain

---

### Post by Nxion on 2008-02-21
But does that affect BOOT UP resolution ?

Now when I am in ubuntu its fine. I want to make the bootup rez smaller. When I say boot up rez I mean when it is loading all the services and what not.

---


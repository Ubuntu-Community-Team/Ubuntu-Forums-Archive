---
title: "fglrxinfo/glxinfo problem"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by proxima estacion on 2007-02-08
When I enter fglrxinfo I get a strange line appearing:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".<----what is this all about???
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

And with glxinfo | grep rendering i get this line as well:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".<---Here he is again!!
direct rendering: No

I'm trying to install Beryl and have dont it on this machine before but never seen this error, needless to say Beryl isnt running at all. any ideas?? thanks all

---

### Post by DSn0wMan on 2007-02-09
It looks like you have not enabled DRI. 

You should have something like the following in /etc/X11/xorg.conf

Section "DRI"
       Mode         0666
EndSection

Please take a look at the beryl wiki - [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_GC_Drivers#ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_GC_Drivers#ATI)

---

### Post by proxima estacion on 2007-02-09
That Tutorial solved it - Thanks!!

---

### Post by proxima estacion on 2007-02-09
Thanks!!!! problem solved

---

### Post by jtbo on 2007-02-09
I do have same problem, only it is saying 0.0:
Xlib: extension "XFree86-DRI" missing on display ":0.0

I'm using Dapper and no any tutorial has helped to resolve this problem so far. 

I don't know if this has something to do with it, found from some Beryl tutorial:
linux-dri-modules-2.6.15-27-386 IS not up, and needs to be fixed.

All I would like to do is to get 3d acceleration for wine working.

---

### Post by aberry5555 on 2007-02-09
This is more than likely because the ATI drivers in the repositories are too old, go to [www.ati.com](www.ati.com) and get the linux drivers from there, then follow the instructions on the site or post back if you need more help :p.

---

### Post by proxima estacion on 2007-02-09
Thanks all - one of those links did the trick cant remember which one im afraid. thanks

---

### Post by jtbo on 2007-02-09
> **aberry5555 said:**
> This is more than likely because the ATI drivers in the repositories are too old, go to [www.ati.com](www.ati.com) and get the linux drivers from there, then follow the instructions on the site or post back if you need more help :p.

You are very right, thanks. 

With new drivers from Ati.com that error message no longer appears. So problem solved and got another to replace it, but that will be whole another story ;)

---


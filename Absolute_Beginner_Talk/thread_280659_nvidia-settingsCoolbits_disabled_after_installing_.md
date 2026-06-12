---
title: "nvidia-settings/Coolbits disabled after installing comiz/XGL/Beryl"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-19
After installing Compiz/XGL/Beryl, the command "nvidia-settings", although it opens a "NVIDIA X Server Settings" window, it doesn't contain all the options it used to contain ](*,) . Anyway, here's a pic:

[[IMG]http://img155.imageshack.us/img155/4811/untitledxw0.th.png[/IMG]](http://img155.imageshack.us/my.php?image=untitledxw0.png)


I'd really like to have all the options, specially Coolbits since OCing makes a HUGE difference with my **_CHEAP_** card (It's one of NVIDIA's 7 series but I'm even ashamed of saying its name... you guys could easily guess, heh).
Hopefully a solution to this is as simple as the solutions for the other problems I've encountered.

Thanks in advance!

---

### Post by Dual Cortex on 2006-10-19
god, my q's always need a little bump to be answered...

*bump*

---

### Post by Dual Cortex on 2006-10-19
2nd bump!!

oh noes!

---

### Post by distroman on 2006-10-19
bumpy :D

Xgl/beryl don't support direct rendering.

```
glxinfo | grep direct
```
Should give you -
```
direct rendering: No
```
So the best way to get it would be to set Xgl/beryl up as a session. 

Accordingly to post #7
[http://forum.beryl-project.org/topic-4861-howto-install-beryl-dapper-nvidia-using](http://forum.beryl-project.org/topic-4861-howto-install-beryl-dapper-nvidia-using)

If you have set it up without a session already you'll need to undo it, you can just comment it, then follow post #7.
```
/etc/gdm/gdm.conf-custom

#0=Xgl

[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel #xv:fbo
#flexible=true
```
Then you should be able to choose between a gnome or Xgl session at the login screen. 

Or you could wait a few days and upgrade to edgy. 
Then you can use this one -
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)
and you'll be able to run beryl with direct rendering.

---

### Post by Dual Cortex on 2006-10-19
Is there an official release date for Edgy?
wait I just found out, Oct 29...

---

### Post by Dual Cortex on 2006-10-19
Ok, so what you are telling me to do is to creat another session so I can use the nvidia settings?
Well I was expecting to be able to use both at the same time but I guess it's not possible. I'll just have to wait for edgy!

---


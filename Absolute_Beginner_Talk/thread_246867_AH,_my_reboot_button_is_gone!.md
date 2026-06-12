---
title: "AH, my reboot button is gone!"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by wsun on 2006-08-29
Hi guys, I noticed something strange yesterday night before going to sleep. when I click the "logout,reboot,switch user" icon in the top right corner, I don't have "shutdown" or "reboot" anymore... All I have is switch user, logout and hibernate. What is going on?

---

### Post by akniss on 2006-08-29
Try going to   System -> Preferences -> Sessions and make sure there is a checkmark beside "Ask on Logout"

---

### Post by wsun on 2006-08-30
yeah there already is a check in the box..

---

### Post by Senshi on 2006-08-30
Do you log into the default session or something different on startup?

---

### Post by Dinerty on 2006-08-30
Have you recently installed xgl/compiz, as this removes the shutdown and reboot buttons, this is a known bug.

---

### Post by bullgr on 2006-08-30
if you have recently installed xgl/compiz the shutdown and restart buttons are gone... this is a common bug...
i searched all the forum, in google but there is not any solution for now... the only we can do is wait...

you can use the terminal to avoid the logout/shutdown-reboot procedure...

> sudo halt
shutdown the pc and
> sudo reboot
reboot the pc

---

### Post by wsun on 2006-08-30
thanks... I think I installed compiz so that's why it is gone ](*,)

---

### Post by wsun on 2006-08-31
if I uninstalled compiz would I gain it back?

---

### Post by BoyBlunder on 2006-09-07
has this error been fixed at all? i'm experiencing the same thing at the moment, and i need to type in startx whenever i reboot :\

---

### Post by jordanmthomas on 2006-09-07
I don't even know that it's really a bug per se.
If you install XGL and compiz according to most guides, it will make two XServers, with XGL being the second one.  The shutdown / restart option is only on the first XServer.

wsun, to answer your question...if you undo whatever part you did to make XGL start instead of normal X, your buttons will return.

BoyBlunder, have you tried installing XGL and failed or something?  I'm not entirely sure of what your trouble is.

---

### Post by BoyBlunder on 2006-09-07
yea, i failed, and had to reconfigure xorg. typed in "startx" and it came to the gui desktop and when i wanted to shut down, the button wasn't there, so i don't know what's up :\

---

### Post by jordanmthomas on 2006-09-07
Did you follow a guide?
If so, which one?
If I can find out what you did I will probably be able to help you fix it.

---

### Post by BoyBlunder on 2006-09-07
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

the one from there.

thanks jordan :]

---

### Post by jordanmthomas on 2006-09-07
okay,

```
gksu gedit /etc/gdm/gdm.conf-custom
```

Find this:
```
[servers]# Override display 1 to use Xgl
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```

Comment it out to look like this:
```
[servers]# Override display 1 to use Xgl
[COLOR="Red"]#[/COLOR]0=Xgl 

[COLOR="Red"]#[/COLOR][server-Xgl] 
[COLOR="Red"]#[/COLOR]name=Xgl server 
[COLOR="Red"]#[/COLOR]command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
[COLOR="Red"]#[/COLOR]flexible=true
```

Then go to System Administration --> Preferences --> Sessions
In the startup tab, remove or disable your 'thefuture' entry.

Now, everything should atrt up as usual I think.

---

### Post by BoyBlunder on 2006-09-07
worked like a charm.

you're a lifesaver!

---

### Post by jordanmthomas on 2006-09-07
no problem.  glad it worked!

---


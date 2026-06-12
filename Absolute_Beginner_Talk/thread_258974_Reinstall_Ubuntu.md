---
title: "Reinstall Ubuntu"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by knutsack on 2006-09-16
I royally screwed up my Ubuntu playing around with some things... I dont even want to mention what I did, so I just want to Uninstall Ubuntu and reinstall it... Or is there a way i can roll back settings to an earlier date like windows system restore?

I feel increadibly stupid for doing this, but you can only learn by screwing up...

thanks for any help you can give...

---

### Post by deadgobby on 2006-09-16
If it is still stuck at the promt screen before the boot. Asking for root password. Go ahead and login there. Check to see if it is asking to run 
fsck. You may have some broken packs or known as orphans. If it does ask to run fsck then run it. Itr should fix the broken pack or orphans and will boot back up after its completion.
GObby

---

### Post by jordanmthomas on 2006-09-16
fsck doesn't check anything about broken packages.  It checks the filesystem.  It would be a good idea to try it out, but not to fix your broken packages.
```
jordan@jordan:~$ wtf is fsck
fsck: fsck (8)             - check and repair a Linux file system

```


Anyway, unless you have explicitly installed some sort of a 'system restore' there is no such function.  

I know you don't want to say, but what did you do?  It could be possible to fix it...and you would probably learn a lot in doing so.

---

### Post by knutsack on 2006-09-16
Not Exactly sure to be honest...

I tried installing compiz and now when i start up it says it is looking for xserver, and the screen blinks a few times and it will not do anything, just sit there...

I think I may have screwed something up when I put altered stuff in the text editor...

It wont even startup which is why I just wanted to reinstall it

---

### Post by jordanmthomas on 2006-09-16
Which guide did you follow to install compiz?  Chances are it's a simple fix!

---

### Post by knutsack on 2006-09-16
I used the guide from here

[http://doc.gwos.org/index.php/XGL_Compiz%2832bit%29Nvidia](http://doc.gwos.org/index.php/XGL_Compiz%2832bit%29Nvidia)

---

### Post by jordanmthomas on 2006-09-16
You will have to log in on one of the consoles (<Ctrl><Alt>F1-6)
```
sudo nano /etc/gdm/gdm.conf-custom
```
In it, you will see this:
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```
either delete these lines or put a # at the start of each of them

Saving in nano is confusing if you don't know how, so I'll tell you
<Ctrl>X
y
<Enter>
<Enter>

Reboot and see if that does anything for you.  (It may or may not)

---


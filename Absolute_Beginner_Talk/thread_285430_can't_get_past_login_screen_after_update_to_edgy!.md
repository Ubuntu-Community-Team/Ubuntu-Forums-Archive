---
title: "can't get past login screen after update to edgy!"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-26
I'm running an AMD processor, Nvidia video card, and I had XGL/beryl 
installed on dapper. Now after I've upgraded via update manager, I can't get 
past the splash screen after logging in. It plays the welcome sound and just
 stops with a blank tan screen. Please help!!

---

### Post by Rackerz on 2006-10-26
Have you tried just Gnome, no XGL?

---

### Post by shanepardue on 2006-10-26
well, it's in my gnome session. I've tried the failsafe method which I believe doesn't start XGL.

---

### Post by shanepardue on 2006-10-26
I've disabled GLX in xorg.conf and I can get logged in now, but I'm having 
problems. Is anyone getting beryl working in Edgy?

---

### Post by shanepardue on 2006-10-26
Whenever I try to switch to Beryl for my windows manager, it freezes up. Any idea why XGL/Beryl wouldn't work?

---

### Post by shanepardue on 2006-10-26
sorry for the frequent posts, but i found the solution...

edgy had changed my gdm-conf-custom or whatever it is. it took out the server
section that is required for XGL to do it's thing. I'm good to go now!

---

### Post by reazn on 2006-10-30
im having the same problem, will give it a go as you said.

---

### Post by reazn on 2006-10-30
didn't work for me :(

what did you add in?

---

### Post by shanepardue on 2006-10-30
this is what i had to make my server section look like

```
[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```

---


---
title: "Numpad's period key deletes"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-09
When I have numlock on and when I press the "period" key, it deletes and 
doesn't enter a "period". Any idea how to fix this?

---

### Post by ciscosurfer on 2006-11-09
Strange.  Usually when numlock is on, the DEL function is turned off.  Have you recently (on purpose or otherwise) changed your keyboard layout?

---

### Post by shanepardue on 2006-11-09
I don't recall changing my layout. Right now, it's on "US 105-key keyboard 
(with windows keys)"

I was having problems with even getting caps lock and num lock to work in the 
beginning and I think that's an XGL issue. This is what I did to fix that
problem...
```

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer #-kb
flexible=true
```

---

### Post by shanepardue on 2006-11-11
I had to do a clean install of Ubuntu and it works fine now. Not sure what
the problem was.

---


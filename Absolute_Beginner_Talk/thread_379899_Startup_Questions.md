---
title: "Startup Questions"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by jtyker on 2007-03-09
Hey guys,

I have a couple questions on how to change my startup.  When my desktop comes up after startup there are 2 windows open: the session manager and my home folder, I am just curious how I get those to not come up every time.

Thanks

JT

---

### Post by dhughes on 2007-03-09
This may be an odd, and confusing, question on my part but have you somehow put an entry in Startup making Sessions start at Startup?

 Same for your home folder is it in Startup? I'm not even sure if that can be done but I see in mine there is an entry for Evolution showing a path to a file so maybe you can put an entry there to open Home at startup.

---

### Post by nanotube on 2007-03-09
> **jtyker said:**
> Hey guys,

I have a couple questions on how to change my startup.  When my desktop comes up after startup there are 2 windows open: the session manager and my home folder, I am just curious how I get those to not come up every time.

Thanks

JT

see if there are entries for these under system>preferences>sessions>startupprograms, and delete them.

---

### Post by jtyker on 2007-03-09
> **nanotube said:**
> see if there are entries for these under system>preferences>sessions>startupprograms, and delete them.

That was my thought as well, but unless I am mistaken (which is definitely possible) they aren't there

Startup programs:
gaim
update-notifier
beryl-manager
gmail-notify
/usr/lib/evolution/2.8/evolution-alarm-notify
gdesklets
gnome-power-manager
gnome-volume-manager --sm-disable
beagled
nm-applet --sm-disable

---

### Post by dhughes on 2007-03-09
This post: [http://ubuntuforums.org/showthread.php?p=1786026](http://ubuntuforums.org/showthread.php?p=1786026)


 [quote="CatKiller"]  "*I had this for a while too - the session seemed to have been saved at the point that I unticked the "Save Session" box in Session manager. So every time I logged in, it would open Session manager (and Nautilus, and a Terminal window, IIRC). The solution I found was to untick the box, close everything, then press Alt-F2, and then run gnome-session-save. This saved the session at the point where everything was closed, and all has been well since.*" [/quote]

---

### Post by jtyker on 2007-03-09
Perfect, that worked great, thank you

---


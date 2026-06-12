---
title: "Can't get into terminal after messing with nvidia-settings"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by nesty on 2007-08-22
Hi everyone.

I have a bit of a problem here...after deciding to enable xinerama in nvidia-settings and restarting X, I can't open up my terminal anymore.

It starts to boot and I can see it loading, but then nothing happens.  It just doesn't come up.

I would use a real terminal instead of gnome-terminal, but I don't know how to edit my nvidia-settings settings without the GUI.

Anyone know what's going on?

Thanks.

---

### Post by AlexenderReez on 2007-08-22
the easiest way just enter 

> sudo dpkg-reconfigure -phigh xserver-xorg

to go back to default setting:)

---

### Post by fantasyspirit91 on 2007-08-22
That happened to me too. I ended up using the Konsole Terminal.

---

### Post by nesty on 2007-08-22
Thanks everyone, I ended up just making a new xorg.conf.  Konsole worked for me, but it still wouldn't let me open up on gksudo nvidia-settings.

My problem has been solved.  Thank you!

---


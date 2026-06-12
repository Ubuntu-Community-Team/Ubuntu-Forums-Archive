---
title: "questions regarding openbox"
date: 2012-08-14
forum: Any Other OS
---

### Post by neil_1 on 2012-08-14
I've installed openbox on linux mint and it works well. I've a few questions though,
Does anyone know how to correct how notify-send looks ? how can i remove the black border/shadow it has ?

[IMG]http://s11.postimage.org/xaee67mvn/notify_send.png[/IMG]

Also, does anyone know how to get a volume icon in the system tray ?
i have installed xfce4-mixer and pavucontrol but none have an icon with which i can control volume with form the system tray (tint2)

---

### Post by m_duck on 2012-08-14
For the black borders I suspect the issue is that you are missing a compositing manager. Try installing xcompmgr, running it and then sending a notification - hopefully that should fix that.

For volume control in the system tray there are quite a few options, however it looks as though none (that I can find) are available through the software centre. For somewhere to start though: alsa-tray, gtk-vol, gvolwheel, gvtray, pnmixer, pvolwheel, volti (all courtesy of a search of the Arch Linux AUR).

I hope this is of at least *some* use!

---

### Post by Perfect Storm on 2012-08-14
Moved to Other OS/Distro Talk.

---

### Post by neil_1 on 2012-08-14
Thanks!
Got it by installing xcompmgr and running xcompmgr -n &
Also, i installed volwheel

---


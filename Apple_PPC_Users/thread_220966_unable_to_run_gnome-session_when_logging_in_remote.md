---
title: "unable to run gnome-session when logging in remotely from iMac"
date: 2006-07-22
forum: Apple PPC Users
---

### Post by rogerwp on 2006-07-22
I have just installed Ubuntu from scratch on my old laptop.  All works fine and from my intel iMac I connect with  

rwp-mini:~ rwpmini$ ssh -Y roger@192.168.2.10

when connected (from my iMac), I can run programs like xclock and even gdmsetup works fine but gnome-session fails as follows:

roger@192.168.2.10's password: 
Linux omnibook4150 2.6.15-26-686 #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006 i68
6 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sat Jul 22 16:42:38 2006
roger@omnibook4150:~$ 
roger@omnibook4150:~$ 
roger@omnibook4150:~$ 
roger@omnibook4150:~$ 
roger@omnibook4150:~$ gnome-session
SESSION_MANAGER=local/omnibook4150:/tmp/.ICE-unix/4886
Window manager warning: Log level 32: could not find XKB extension.
Window manager warning: Screen 0 on display "localhost:10.0" already has a windo
w manager

(gnome-panel:4904): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `d
est_width > 0' failed

** (nautilus:4906): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS

** (nautilus:4906): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:4906): WARNING **: Can not get _NET_WORKAREA

** (nautilus:4906): WARNING **: Can not determine workarea, guessing at layout
Window manager warning: Log level 32: could not find XKB extension.
Window manager warning: Screen 0 on display "localhost:10.0" already has a windo
w manager

What suggestions to get this working?

---

### Post by rogerwp on 2006-07-23
Found this useful posting:
[http://lists.apple.com/archives/X11-users/2005/Oct/msg00015.html](http://lists.apple.com/archives/X11-users/2005/Oct/msg00015.html)

Seems that it is a conflict between quartz-wm and gnome... Working in full-screen mode it does work a bit better but still not properly.

Only option I can see for now is just to run applications separately, without the benefit of an X11 deskop. This works but getting a desktop to work remotely would be much better.

Any other suggestions?

---


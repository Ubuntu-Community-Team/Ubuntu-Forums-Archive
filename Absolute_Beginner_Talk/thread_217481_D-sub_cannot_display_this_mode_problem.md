---
title: "D-sub: cannot display this mode problem"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by fabsy on 2006-07-17
I tried to install my new Dell widescreen display, followed some (IMO) nice instructions on the web, and after restarting the x-server I get a black screen saying: D-sub Cannot Display this Mode.

Everything works nicely in the background: webcalendar and shared disks etc, but I cannot find out how I will manage to change the settings back to original. 

The root to my problem is that I changed the xorg.conf (which I backed up just in case), and now I get the mentioned black screen (another kind of BSOD, heh?)

Can I restart the computer in text mode and replace the the damaged xorg.conf, or can I somehow repair the system with my Ubuntu 5.10 install CD (there may be a problem though - I have changed Ubuntu to Kubuntu), or is there any other way.

Many thanks in advance!

---

### Post by slimdog360 on 2006-07-17
In the text mode or terminal or whatever
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by fabsy on 2006-07-17
Yes, but how can I log in in text mode? Say for example if I restart the computer, is there any keys I can press and get an option to start without a graphical interface? Now Kubuntu start Ok, but after everything is loaded the screen turns to black with the message "cannot display this mode" (which is a result of stupid me changing the resolution to 1680x1050).

---

### Post by fabsy on 2006-07-17
Never mind, I got it working again... it was only the login page that couldn't be viewed. After typing the login password in blind, Kubuntu started ok, and I replaced the xorg.conf with my backup. 

Damn I'm good, one day might become a real Linux guru ;)

---


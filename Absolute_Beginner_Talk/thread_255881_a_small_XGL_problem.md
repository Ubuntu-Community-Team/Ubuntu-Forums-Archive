---
title: "a small XGL problem"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-09-12
I've managed to install XGL
but when I first login to XGL session I chose x manager and not GNOME as I supposed to
and the windows are now can't be minimized/maximized

how can I change to XGL session to use GNOME and not X ?

---

### Post by MaximB on 2006-09-12
[SIZE=3]I can login to gnome and to XGL
but the XGL uses X and not GNOME as I want it to

how to make it use GNOME ?
[/SIZE]

---

### Post by MaximB on 2006-09-12
and one more thing
I've followed this guide to install XGL
THE SECOND SOLUTION
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

---

### Post by flargen on 2006-09-12
The howto you used is a bit wrong. You do not need to install the package compiz-gnome anymore, so run
```
sudo apt-get remove compiz-gnome
```

You should install compiz-manager (tray icon and autostart) and csm (compiz settings manager)
```
sudo apt-get install compiz-manager
```

Also, where it says to add "compiz-start" to System->Preferences->Sessions etc, write "compiz-manager" instead.

That should get you on the right track...

Can you post the contents of /usr/bin/startxgl.sh and /usr/share/xsessions/xgl.desktop, so I can help you figure out your problem.

Glad to help :)

---

### Post by MaximB on 2006-09-13
srartxgl.sh :
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session


xgl.desktop :

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

and it's working fine now
but I still want it to use gnome

---

### Post by redDEADresolve on 2006-09-13
I used the same guide you did but instead of puting "/user/bin/compiz-start" in to sessions start up, I created a launcher w/ "compiz-start" in the command line.

This allows me to load into gnome everytime i log in, then if I want to use XGL i just click the launcher and it loads up. If i want to get out of it i just log out and then back into session.

I think it works better then creating two session log ins.

---

### Post by MaximB on 2006-09-13
I've done it
but a strange this happens
the "compiz manager" works only when I enter XGL session
and it refuses the change manager when I boot to gnome session
any thought ?

---

### Post by jordanmthomas on 2006-09-13
compiz needs XGL / AIGLX to run.  If you choose your Gnome session, you are loading up normal X, not XGL.  Therefore, compiz won't run.

---

### Post by flargen on 2006-09-13
EDIT - beaten to it

---

### Post by MaximB on 2006-09-13
so I just need to always login to XGL and change it from there

---

### Post by brendo on 2006-09-13
Heres a little xgl problem that has been driving me totally nuts for the past two days:

I have installed all of the compiz packages and have glx running on my computer correctly. However, when I try to start compiz with

```

compiz-start

```

I read the following from nohup.out:

```

The application 'cgwd' lost its connection to the display :1.0; most likely the X server was shut down or you killed/destroyed the application.

```]

and if I start the compiz-manager, I can try to select compiz as the window manager, but when I select it the windows disappear and reappear, but metacity is still selected and running.

How can I fix this? I have been combing through the forums for hours and I can't find the answer...(*,)

---

### Post by jordanmthomas on 2006-09-13
```
ps -A | grep X
```
Are you running normal X or one of the compiz-worthy ones?

---

### Post by brendo on 2006-09-13
i get:

```
4436 tty7    00:00:12 Xorg
```

---

### Post by jordanmthomas on 2006-09-13
Compiz won't run on stock Xorg.
You need to be running XGL or Xorg-air (AIGLX)
DId you follow a tutorial to install compiz or did you do it on your own?  
It shouldn't be hard to fix your issue.

---


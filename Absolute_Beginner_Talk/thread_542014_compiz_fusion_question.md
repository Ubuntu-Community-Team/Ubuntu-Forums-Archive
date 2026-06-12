---
title: "compiz fusion question"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by ac1240 on 2007-09-03
i have followed this guide
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
did everything in the guide 
(no errors come up) but the compiz fusion doesnt work 
i am seeing the ubuntu original desktop without any new effects

after writing this in the terminal
compiz --replace
i am getting this
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by meindian523 on 2007-09-03
That error means you didn't install XGL.

Do```


sudo apt-get install xserver-xgl
```

ONLY if you are using proprietary drivers.

Then there's a small script for making Xgl run on startup and to enable a option of Gnome with Xgl in your sessions menu when you login.

Do
```

gksudo gedit /usr/local/bin/startxgl.sh
```

Enter this in the gedit window

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

Save and exit.

Make the script executable with 
```

gksudo chmod a+x /usr/local/bin/startxgl.sh
```

For the Gnome with Xgl session:
```

gksudo gedit /usr/share/xsessions/xgl.desktop
```

Enter this in the gedit window
```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Make this script executable too..
```

gksudo chmod a+x /usr/share/xsessions/xgl.desktop
```

Then reboot,select Gnome with Xgl session from your sessions menu(find the sessions menu in the options button in the left bottom,and on login do compiz --replace.And voila!

---

### Post by ac1240 on 2007-09-03
nothing happend after i wrote 
gksudo chmod a+x /usr/local/bin/startxgl.sh
and
gksudo chmod a+x /usr/share/xsessions/xgl.desktop
in the terminal window is that ok?

---

### Post by Paul133 on 2007-09-03
Ah. You don't appear yto be in an XGL session. Log out and then log back in but under sessions, choose XGL.

edit: You installed XGL right?

---

### Post by Nythain on 2007-09-03
probably, though you really shouldnt gksudo the chmod command, at least i dont see why you would... id probably just sudo it since its not really a graphicall app... but hey... but yeah, in a nutshell chmod doesnt really usually give any output as to what it did, so nothing "appearing" to happen would be pretty normall... you could check the permissions of the file by opening up nautilus (or whatever gnomes file browser/manager is called) and right clicking on the file, going down to what should be called "properties" selecting a tab or option "permissions" and making sure its executable... thats all the chmod command did in a nutshell, was made it so everyone can execute it

---

### Post by sailor2001 on 2007-09-03
compiz --replace is written in alt/f2 not the terminal

---

### Post by ac1240 on 2007-09-03
k i manged ty allllllllllllll i love you :)
the xgl soved also my watiching tv from computer problem 
i know i have been an annoin guy today :)

---

### Post by bosp7 on 2007-09-03
I was having the same problems and after I did the steps listed by meindian523, and logged in with a xgl session my display is all messed up.  It looks almost like static at first and then all jumbled.  Any ideas?

---

### Post by meindian523 on 2007-09-04
> **bosp7 said:**
> I was having the same problems and after I did the steps listed by meindian523, and logged in with a xgl session my display is all messed up.  It looks almost like static at first and then all jumbled.  Any ideas?

Are you using proprietary drivers?What's your graphic card model?The above steps are ONLY for people using proprietary drivers......

---


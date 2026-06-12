---
title: "Need help with XGL and printing"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by wak_wak on 2007-08-08
I'm a newb so forgive me for stupidity...

I installed Kubuntu.  All is good.

I install XGL and almost all is good.

3 problems:

1)  Can't shutdown within Gnome XGL.  Can only log out and then shut down from the log in window.

2)  If I log out and then log back in it's all messed up.  I've got compiz fusion running and it's great until I log out and then log back in.  It'll be there but very messed up looking.

3)  I can't find the printer icon.  The one to find new printers.  CUPS is installed and everything.  If I'm inn KDE I can see it but it's missing when I'm in Gnome XGL.

Please help.

---

### Post by Al3xK3aton on 2007-08-08
1. Just shut down from the login window. It's easier than fixing the problem.

2. Don't log out and back in, just restart every time. It's easier than fixing the problem.

3. Just add new printers through KDE. It's easier than fixing the problem.

---

### Post by AlexenderReez on 2007-08-08
hello there :)....

i think i have experience this kind of situation before...i guess you may use startxgl.sh script sort of


```


#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---> this is what you will get if refer to most of the guide in wiki/howto ...[/B]

change it to 

```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
sleep 3
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```
[B]
and don't forget to execute it again :)

> sudo chmod a+x /usr/local/bin/startxgl.sh

---

### Post by wak_wak on 2007-08-08
I did that but all it did was add a gray background while XGL was starting.  But still no ability to add a printer or shutdown without logging out 1st.

Here's the copy of the startxgl.sh file:

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
sleep 3
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session


#!/bin/sh
#Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
#DISPLAY=:1
#cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
#xauth -i add :1 . "$cookie"
#exec dbus-launch --exit-with-session gnome-session


I kept the original in there and just commented all the old out. 

Any other ideas?

---

### Post by wak_wak on 2007-08-09
> **Al3xK3aton said:**
> 1. Just shut down from the login window. It's easier than fixing the problem.

2. Don't log out and back in, just restart every time. It's easier than fixing the problem.

3. Just add new printers through KDE. It's easier than fixing the problem.




Funny...:)

---

### Post by wak_wak on 2007-08-10
HELP!  Any ideas anyone???

---

### Post by wak_wak on 2007-08-13
So kaddprinterwizard does work from the CLI.  So I guess what I need to be able to do is figure out how I'd add items to my menus.

????

---

### Post by wak_wak on 2007-08-14
Bump?

---


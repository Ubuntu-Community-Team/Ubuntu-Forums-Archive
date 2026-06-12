---
title: "can´t log in"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by TwoHybrid on 2007-03-12
hi everybody,

i´m totally new to this, so please help:

i just installed xubuntu on an old machine (amd 350mhz, 64mb ram) with the text modus on the alternate cd.

now, after installation and rebooting the log on-screen appears, which seems to be ok 8). when i type in my username and password, the log-on-box disappears, the background-picture appears, and the mousecursor turns into a spinning sign, which seems to be normal too, i think. but then the screen turns white for half a second and then the log on-screen appears again.

i cannot log in. always the same procedure.

so, where´s my mistake? can anybody help?

---

### Post by XstatyK on 2007-03-12
try logging in to the console itself first.  I think its CTL SHIFT F1 or CTL ALT F1 then log in there.
After you are able to log in successfully then type startx and see what results you get.

---

### Post by TwoHybrid on 2007-03-12
ok, here we go. this is what i get then:

xauth: creating new authority file /home/myname/.serverauth.4097
xauth: creating new authority file /home/myname/.xauthority
xauth: creating new authority file /home/myname/.xauthority


Fatal server error:
Server is already active for display 0[INDENT]If this server is no longer running, remove /tmp/.X0-lock
and start again.[/INDENT]

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit: unable to connect to X server
xinit: No such process (errno 3): Server error.

i don´t understand anything of this

btw: thx 4 your help xstatyk

---

### Post by XstatyK on 2007-03-13
Sorry I didn't respond sooner, got a little tied up

Well let's see what we can do.
First lets log in again as you did before but before you startx lets try and remove the lock file

```
sudo rm -f /tmp/.X0-lock
```

Then do 

```
sudo Xorg -configure
```

Then finally do

```
shutdown -r now
```

Then hopefully it will come back up.  If not I am at a loss but I would say if that doesn't work maybe posting your Xorg.conf file so we can take a look and maybe someone can spot something else.

---


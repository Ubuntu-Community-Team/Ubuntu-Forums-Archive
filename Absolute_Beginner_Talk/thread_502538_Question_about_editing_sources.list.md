---
title: "Question about editing sources.list"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-07-16
Apparently, I can't do so. I'm using Knoppix 3.8, and everytime I try to modify it, I get this:

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0


---

### Post by aysiu on 2007-07-16
How are you trying to modify it? Are you doing a right-click and *Edit as Root*? Are you using the command ```
kdesu kate /etc/apt/sources.list
``` from the terminal?

---

### Post by ARandomKid on 2007-07-16
Second one, from terminal.

---

### Post by ARandomKid on 2007-07-16
Bump for the night...

---

### Post by aysiu on 2007-07-16
I don't know that Knoppix uses *kdesu*. Doesn't it have a root account?

Try ```
su
kate /etc/apt/sources.list
```

---

### Post by ARandomKid on 2007-07-16
;x_X Makies it even more confuzzling.

> Link points to "/tmp/ksocket-root"
mkdir: Owner of /tmp/.ICE-unix should be set to root
QPixmap: Cannot create a QPixmap when no GUI is being used
QPixmap: Cannot create a QPixmap when no GUI is being used
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-31561' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-31542' to 'kate'
kate: ERROR: Communication problem with kate, it probably crashed.


And I"ve still go that first problem..."cannot connect to X server"

---

### Post by ARandomKid on 2007-07-17
;_; Why must this be made so incredibly difficult to solve? All I wanna do is edit the sources file...is that really so much to ask? ;_;

;>.>

---

### Post by bodhi.zazen on 2007-07-17
Either :

sudo nano -B /etc/apt/sources.list

Or

sudo vi /etc/apt/sources.list


Nano will be easier to use. When you are done editing hit Ctrl-X to exit, type "Y" to save your changes. The -B flag will make a backup at /etc/apt/sources.list~

---


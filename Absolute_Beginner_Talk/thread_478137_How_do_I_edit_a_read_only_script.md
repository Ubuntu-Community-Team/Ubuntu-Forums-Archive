---
title: "How do I edit a read only script?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-19
I was following a guide which instructed me to enter following and then to enter the next stuff into a text editor.
```

gksudo gedit /usr/bin/startxgl.sh

```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session


I screwed up and mistakenly added some lines that weren't  suppose to be there and saved the file and now I cannot edit it because its a read only and some how i don't have permission to make the changes.

Could some one please tell me edit a read only file


Thanks in advance,

VC

---

### Post by eentonig on 2007-06-19
just enter 
> gksudo gedit /usr/bin/startxgl.sh

again. You will get a prompt to enter your password. And then you should be able to make the changes.

---

### Post by Stephen Howard on 2007-06-19
put 'sudo' in front of the command - then you'll be prompted for your password and be able to edit and save the file.

You probably sudo'ed it when you edited it the first time, otherwise a normal user can't change stuff in /bin

---

### Post by videocheez on 2007-06-19
thanks guys  btw, what does the gk in front of the sudo mean?

---

### Post by PaulFr on 2007-06-19
gksu  is a frontend to su and gksudo is a frontend to sudo. So you can avoid having to start up a terminal and using command line tools.

In general, if you want to find out about a command, try **man <command>** in a terminal - usually you will get a lot of information about the command and the options available. 

I just realized you can also get the *man* pages from the System -> Help and Support menu option. Select **Advanced Topics**, the last option in the Topics menu, then you will select the Terminal Command References (man pages).  Hope this helps.

---

### Post by bodhi.zazen on 2007-06-19
LOL

gk is used when you want to run graphical programs as root (su or sudo).

On distors that use sudo the command will be gksudo, otherwise gksu.

This is a good run-down : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by videocheez on 2007-06-19
thx guys

---

### Post by Golyadkin on 2007-06-19
If you want to make a file no longer readonly, you can change it's permissions with this command:
> 
sudo chmod u+w filename


---


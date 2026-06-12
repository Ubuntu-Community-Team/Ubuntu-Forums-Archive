---
title: "what does evn do?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-19
when i type env i get a list of variables
how can i edit them??

thanks

ps heres my list:


SSH_AGENT_PID=5065
TERM=xterm
SHELL=/bin/bash
GTK_RC_FILES=/etc/gtk/gtkrc:/home/freeth/.gtkrc-1.2-gnome2
WINDOWID=37748743
USER=freeth
SSH_AUTH_SOCK=/tmp/ssh-dghDud5023/agent.5023
GNOME_KEYRING_SOCKET=/tmp/keyring-mfM6ZP/socket
USERNAME=freeth
SESSION_MANAGER=local/nephroid:/tmp/.ICE-unix/5023
KONSOLE_DCOP=DCOPRef(konsole-5854,konsole)
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
KONSOLE_DCOP_SESSION=DCOPRef(konsole-5854,session-1)
PWD=/home/freeth/.cairo-dock
LANG=en_US.UTF-8
GDMSESSION=default
SHLVL=2
HOME=/home/freeth
LANGUAGE=en
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=freeth
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-TKrMdOcy0S,guid=238f10457ae5933dd8951417a7696e00
DISPLAY=:1.0
COLORTERM=
XAUTHORITY=/tmp/.gdm2tb5No
_=/usr/bin/env

---

### Post by croak77 on 2006-09-19
What do you want to change?

---

### Post by jinxjinx on 2006-09-20
i want to change PWD

---

### Post by RoyArne on 2006-09-20
> **jinxjinx said:**
> i want to change PWD

PWD is your working directory. It is set every time you use the **cd** (change direcory) command, but if you can change PWD by writing PWD=*pathname*.

Write
```
PWD=/etc
```
to change directory to /etc; **cd /etc** will accomplish the same.

---

### Post by jinxjinx on 2006-09-20
oh i see. for some reason each time i run konsole i start in a dir other than my home dir. any idea how to change this?

thanks

---

### Post by skymt on 2006-09-20
What directory does Konsole start in?

---

### Post by jinxjinx on 2006-09-21
home/freeth/.cairo-dock

i think its because of this start up script:

#!/bin/bash
cd ~/.cairo-dock
./cairo-dock --no-glitz --no-background&
cd ~

---


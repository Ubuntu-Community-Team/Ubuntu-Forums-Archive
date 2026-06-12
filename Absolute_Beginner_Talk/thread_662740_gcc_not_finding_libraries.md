---
title: "gcc not finding libraries???"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by jmenard on 2008-01-09
I'm trying to compile a c program that i wrote for class. This is the first time i've tried to write anything in c, and i'm still pretty new to linux. from the error messages that I've been getting it seems like I don't have some path variable set correctly. This is only a guess, and even if I'm right I have no I idea of how to fix it. The program that I'm trying to compile is the first program out of Pointers on C by Reek. When I try to compile the program I get the following errors.

jmenard@jmenard-laptop:~/Documents/ics250$ gcc basic.c
basic.c:2:19: error: stdio.h: No such file or directory
basic.c:3:20: error: stdlib.h: No such file or directory
basic.c:4:20: error: string.h: No such file or directory
basic.c: In function ‘main’:
basic.c:20: error: ‘NULL’ undeclared (first use in this function)
basic.c:20: error: (Each undeclared identifier is reported only once
basic.c:20: error: for each function it appears in.)
basic.c:21: warning: incompatible implicit declaration of built-in function ‘printf’
basic.c:23: error: ‘ouput’ undeclared (first use in this function)
basic.c:26: error: ‘EXIT_SUCCESS’ undeclared (first use in this function)
basic.c: In function ‘read_column_numbers’:
basic.c:34: warning: incompatible implicit declaration of built-in function ‘scanf’
basic.c:39: warning: incompatible implicit declaration of built-in function ‘exit’
basic.c:39: error: ‘EXIT_FAILURE’ undeclared (first use in this function)
basic.c:41: error: ‘EOF’ undeclared (first use in this function)
basic.c: In function ‘rearrange’:
basic.c:53: warning: incompatible implicit declaration of built-in function ‘strlen’
basic.c:64: error: ‘nchrs’ undeclared (first use in this function)
basic.c:67: warning: incompatible implicit declaration of built-in function ‘strncpy’
basic.c: At top level:
basic.c:72: error: expected identifier or ‘(’ before ‘}’ token

Here are what i think my environment variables are:

jmenard@jmenard-laptop:~/Documents/ics250$ env
SSH_AGENT_PID=5729
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
XDG_SESSION_COOKIE=621f3b89bd5942977fe65b00477d5c00-1199887377.232204-453393182
GTK_RC_FILES=/etc/gtk/gtkrc:/home/jmenard/.gtkrc-1.2-gnome2
WINDOWID=50331729
USER=jmenard
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
SSH_AUTH_SOCK=/tmp/ssh-ABxFtX5694/agent.5694
GNOME_KEYRING_SOCKET=/tmp/keyring-yoSBhp/socket
SESSION_MANAGER=local/jmenard-laptop:/tmp/.ICE-unix/5694
USERNAME=jmenard
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/jmenard/Documents/ics250
LANG=en_US.UTF-8
GNOME_KEYRING_PID=5691
GDM_LANG=en_US.UTF-8
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/jmenard
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=jmenard
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-YCFrzZ5PYW,guid=8a664d2200b9e621dfb7d1004784d413
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/jmenard/.Xauthority
_=/usr/bin/env
OLDPWD=/home/jmenard/Documents


So... what do I need to do? Any help would be much appreciated. Thank you,
Jared

---

### Post by ikonia on 2008-01-09
install the "build-essential" package to include the development libs and base headers.

---


---
title: "Ploblems installing Gphoto2 in Fiesty"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Zooey2 on 2007-05-09
I have an I-River T-10 MP3 player Gphoto claims that it can recognize it.
I have installed the library which I believe is /usr/lib/libgphoto2 correctly.


Currently my Camera is recognized.

I have tried to install gphoto2, but keep on getting error messages that I can not understand.

Here is how I started:

ron@ron-desktop:~$ PKG_CONFIG_PATH=/usr/lib/pkgconfig:/usr/local/lib/pkgconfig
ron@ron-desktop:~$ export PKG_CONFIG_PATH

I then ran env and received the following:

ron@ron-desktop:~$ env
SSH_AGENT_PID=5049
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
GTK_RC_FILES=/etc/gtk/gtkrc:/home/ron/.gtkrc-1.2-gnome2
WINDOWID=44100392
USER=ron
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36i=40;33:s o=01;35:do=01;35:bd=40;33;01:cd=40;33;01r=40;31; 01:su=37;41:sg=30;43:tw=30;42w=34;42:st=37;44:ex =01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=0 1;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:* .gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.ja r=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp =01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=0 1;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01 ;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01; 35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:* .xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*. mpc=01;35:*.ogg=01;35:*.wav=01;35:
SSH_AUTH_SOCK=/tmp/ssh-tBHGBz5011/agent.5011
GNOME_KEYRING_SOCKET=/tmp/keyring-Ngv3bH/socket
SESSION_MANAGER=local/ron-desktop:/tmp/.ICE-unix/5011
USERNAME=ron
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/ron
LANG=en_US.UTF-8
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/ron
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=ron
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-pD39vYkfD9,guid=5bc228a159678ef3f87c42004641e3f2
PKG_CONFIG_PATH=/usr/lib/pkgconfig:/usr/local/lib/pkgconfig
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/ron/.Xauthority
_=/usr/bin/env
============================
I then ran ./configure and saw:

ron@ron-desktop:~$ CD /home/ron/Desktop/gphoto2-2.3.1 sudo ./configure
password:
=======================================
Final error message

checking for dynamic library extension... .so
checking pkg-config is at least version 0.9.0... yes
checking for libgphoto2 to use... autodetect
checking for LIBGPHOTO2... checking libgphoto2 config program... gphoto2-config
checking for gphoto2-config... no
configure: error:
PKG_CONFIG_PATH=/usr/lib/pkgconfig:/usr/local/lib/pkgconfig
LIBGPHOTO2_LIBS=
LIBGPHOTO2_CFLAGS=

* Fatal: gphoto2 command line interface requires libgphoto2 >= 2.2.1.4 to build.
*
* Possible solutions:
* - set PKG_CONFIG_PATH to adequate value
* - call configure with LIBGPHOTO2_LIBS=.. and LIBGPHOTO2_CFLAGS=..
* - call configure with one of the --with-libgphoto2 parameters
* - get libgphoto2 and install it:
=========================================

I check under the File Manager and found:
/usr/lib/blibgphoto2

Under /usb.lib/pkgcongig
I found a few files plus 2 sub idirectories of Python 2.4 & Python 2.5

I am lost, and would appreciate help.
I am moving over from windows, which I understand, and now I am very confused.

Please advise,
Ron
Forward Message

---


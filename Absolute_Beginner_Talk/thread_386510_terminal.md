---
title: "terminal"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-03-17
Is there any where i can find out commands for the terminal. I'm new to ubuntu 5.10 and haven't really had a chance to look around at things. 
Thanks

---

### Post by nereid on 2007-03-17
You still use 5.10? Why haven't you upgraded your version of Ubuntu?

About Terminal commands:

[http://freeengineer.org/learnUNIXin10minutes.html](http://freeengineer.org/learnUNIXin10minutes.html)
[http://truehacker.blogspot.com/2006/11/200-linux-commands-for-newbbies.html](http://truehacker.blogspot.com/2006/11/200-linux-commands-for-newbbies.html)
[http://www-128.ibm.com/developerworks/aix/library/au-badunixhabits.html](http://www-128.ibm.com/developerworks/aix/library/au-badunixhabits.html)

Abd for the advanced user:
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

---

### Post by cookieforyou on 2007-03-17
Try
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)
and
[http://linuxcommand.org/learning_the_shell.php#contents](http://linuxcommand.org/learning_the_shell.php#contents)

---

### Post by mikewhatever on 2007-03-17
[http://www.linux.org.mt/node/49#N10025](http://www.linux.org.mt/node/49#N10025)
just to get you started

---

### Post by Dark-Angel on 2007-03-17
i don't think my computer would handle 6.10. It's very old

---

### Post by Wikzo on 2007-03-17
Then try Xubuntu, which is a light version of Ubuntu :)

---

### Post by Dark-Angel on 2007-03-17
ok i might look at that then:)

---

### Post by STREETURCHINE on 2007-03-17
BREEZY BADGER IS NOT A BAD DISTRO I WISH I STILL HAD A COPY.I HAVE BEEN LOOKING FOR AN ISO TO DOWNLOAD FOUND A COUPLE BUT THEY STOP HALFWAY THROUGH THE DOWNLOAD

ANY WAY HERE ARE A FEW

```
#some basic commandline  stuff#

1/   list your hardware->lspci
2/ list your files  ->ls -l
3/ edit fstab  ->gksudo gedit /etc/fstab
4/ edit sources.list  ->gksudo gedit /etc/apt/sources.list
5/ reconfigure xorg.conf  ->gksudo dpkg-reconfigure xserver-xorg
6/ update  ->sudo aptitude update
7/ upgrade ->sudo aptitude upgrade
8/ clean disk ->sudo aptitude autoclean
9/ install packages ->gksudo dpkg -i (package name).deb
10/ uninstall ->cd~ /package name/uninstall

```

```

FILES:
/var/log/messages
/etc
/etc/profile
/etc/inittab
/etc/fstab
/dev
```

```
COMMANDS:
man
man -k 
updatedb
locate
sudo
grep
cat
dmesg
ls -a
ps
ps -ef
tail
tail -f
lsmod
modprobe
lshal
hal-device-manager
tar
apt-get update
apt-get upgrade
```

HOPE THEY ARE OF SOME HELP

---

### Post by nereid on 2007-03-17
STREETURCHINE why are you screaming?

I think you don't understand that the Xserver is just another program which runs on top of the system. You could also use another window manager or desktop environment if you think that GNOME or KDE is too much for your machine.

Just update your distribution to whack some bugs and fill up some security holes. Then you can decide whether GNOME is too slow and what you can do about that or change the window manager to a lighter one, like Fluxbox or the light desktop environment xfce.

---

### Post by mcduck on 2007-03-17
> **Dark-Angel said:**
> i don't think my computer would handle 6.10. It's very old

New Ubuntu versions are not heavier than older ones. Actually quite the opposite. Besides, the support for 5.10 is going to end in April so you'd better upgrade before that..

---

### Post by STREETURCHINE on 2007-03-26
> **nereid said:**
> STREETURCHINE why are you screaming?

I think you don't understand that the Xserver is just another program which runs on top of the system. You could also use another window manager or desktop environment if you think that GNOME or KDE is too much for your machine.

Just update your distribution to whack some bugs and fill up some security holes. Then you can decide whether GNOME is too slow and what you can do about that or change the window manager to a lighter one, like Fluxbox or the light desktop environment xfce.

if you think that is loud then you aint seen nothing sunshine,,lol

just didnt realise my caps lock was on when i created the acc ,now it is to late to change,so you will just have to get over it...:lolflag:

---

### Post by Papa-san on 2007-03-26
On my particular machine, I found 5.10 to be vastly superior to Dapper. I have the disc and am just trying how to build a download section with some of the excess space and monthly bandwidth that I pay for.

---

### Post by x1a4 on 2007-04-19
Hi,

As with any other operating system, most 'commands' are programs without a GUI, with a few built-in to the shell.  Look in 

/bin/
/sbin/
/usr/bin/
/usr/sbin/
/usr/local/bin/
/usr/local/sbin/
/usr/games/
/usr/X11R6/bin/

to find out what 'commands' you have on your system.  To find out what each does run 

*<command> --help*
or *man <command>*

and if you have GNU Info installed 

*info <command>*
*info coreutils <command>*

I also recommend you upgrade, to Edgy at least, and simply use a light-weight GUI.  Xfce or, if even Xfce gives you performance issues, MatchBox--very lightweight, but with features.

---


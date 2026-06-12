---
title: "HELP Gnome gone crazy"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by vaio pcgfxa53 dapper on 2006-12-15
HI all i am in the middle of a unbutu freakout.  I gave microsift the finger for Dapper and i am damn happy but i have been dealing with more problems than i can handle.

Anyways, my question/problem is that whenever i use commands like 'gedit' or any other command line code to launch Gnome I get a permission problem.  Permission is denied regardless of sudo or not. 

Also if i try and launch a file in gnome the text editor box does not open.  If I manualy go to a root file to edit it i have olny read permission and am unable edit.  here are a few samplels of what i am running into;

boss@boss-laptop:~$ /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied
boss@boss-laptop:~$ sudo -i
Password:
root@boss-laptop:~# /etc/resolv.conf
-bash: /etc/resolv.conf: Permission denied
root@boss-laptop:~# dedit /etc/resolv.conf
-bash: dedit: command not found
root@boss-laptop:~# /etc/modprobe.d
-bash: /etc/modprobe.d: is a directory
root@boss-laptop:~# /etc/dhcp3/dhclient.conf
-bash: /etc/dhcp3/dhclient.conf: Permission denied
root@boss-laptop:~# alias net-pf-10 off
-bash: alias: net-pf-10: not found
-bash: alias: off: not found
root@boss-laptop:~# /etc/modprobe.d/badlist
-bash: /etc/modprobe.d/badlist: No such file or directory
root@boss-laptop:~# /etc/modprobe.d
-bash: /etc/modprobe.d: is a directory
root@boss-laptop:~#

---

### Post by mcduck on 2006-12-15
in those examples you don't actually have any command to do anything..

to open a file for editing as root (with gedit), run 'gksudo gedit /path/to/yourfile'

---

### Post by vaio pcgfxa53 dapper on 2006-12-15
Thanks i figured it was something like that but still having a problem (see error log) editor will still not open.

root@boss-laptop:~# gksudo gedit /etc/dhcp3/dhclient.conf
(gksudo:21700): Gtk-WARNING **: cannot open display:



cheers

---

### Post by mcduck on 2006-12-15
That sounds like you are trying to use gedit in Command line, without Gnome running?

Gedit is graphical text editor, so it won't work from command line.

You can use 'sudo nano /path/to/yourfile' instead.

edit: also, if you are alredy rnning as root (or 'sudo -i') there's no need to use 'sudo' or 'gksudo' any more. (sudo is for command line apps, gksudo for graphical apps)

---

### Post by vaio pcgfxa53 dapper on 2006-12-15
worked!  Cheers man thanks a bunch

---

### Post by zappafrank on 2006-12-15
use sudo -s instead of sudo -i, then you can also start graphical programs from a root shell. 

ubuntu~ $ sudo -s
Password:
ubuntu~ # gedit /etc/resolv.conf

i would suggest using nano instead of gedit though, because you'll be able to fix things if your graphical desktop is broken, or you have a text-only connection to another machine. nano is very easy to use, just try it. :)

---


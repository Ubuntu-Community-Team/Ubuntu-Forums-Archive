---
title: "Ubutu 6.06 Server- problem with x-server"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by z1riuz on 2007-09-21
Hi, i`m new in Linux

I have a server running Ubuntu 6.06, i want to run it in Graphical Mode, so i installed Gnome by apt-get and the x-server, then i rebooted and typed startx.
This is the message i get:


root@89-149-240-37:~# startx
xauth:  creating new authority file /root/.serverauth.5105

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux 89-149-240-37.internetserviceteam.com 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 21 21:49:13 2007
(==) Using config file: "/etc/X11/xorg.conf"
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory

---

### Post by juantovarm on 2007-09-23
1- did you install gdm? (gnome display manager), check by installing it via terminal:
sudo apt-get install gdm
2- what graphics card are you using? do you have the right drivers? remember, not all graphic cards run properly under linux
3- type the in the terminal and follow the instructions: sudo dpkg-reconfigure xserver-xorg

just another question, since you are using 6.06 have you upgraded your software?
sudo apt-get upgrade

Just read in ubuntu-es forum: is your partition full? if so, you might want to free some space as the author of the post did 
in spanish [http://www.ubuntu-es.org/index.php?q=node/24437](http://www.ubuntu-es.org/index.php?q=node/24437)
to check disk space type:
df -h

hope that helps
Juan

---


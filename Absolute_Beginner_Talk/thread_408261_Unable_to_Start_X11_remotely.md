---
title: "Unable to Start X11 remotely"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Budha on 2007-04-13
I have ben having this problem since installing KUbuntu (Actually tried Ubuntu, Kubuntu and Xubuntu!!).

I am accesing the server remotely over SSH with Putty and have X11 forwarding enabled over both Putty and in the SSH config file on the server.

When I try and Run an X session, I get the following

(startkde)

++++++++++++++++++++++++++++++++++++++++++++
budha@crunchiii:~$ startkde
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
xsetroot:  unable to open display 'localhost:10.0'
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
xset:  unable to open display "localhost:10.0"
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
xsetroot:  unable to open display 'localhost:10.0'
startkde: Starting up...
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
ksplash: cannot connect to X server localhost:10.0
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
kded: cannot connect to X server localhost:10.0
DCOP aborting call from 'anonymous-6616' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
kcminit: cannot connect to X server localhost:10.0
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
ksmserver: cannot connect to X server localhost:10.0
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
startkde: Done.
++++++++++++++++++++++++++++++++++++++++++

(startx)
++++++++++++++++++++++++++++++++++++++++++
budha@crunchiii:~$ startx
xauth:  creating new authority file /home/budha/.serverauth.6051
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
++++++++++++++++++++++++++++++++++++++++++

(sudo startx)
++++++++++++++++++++++++++++++++++++++++++
budha@crunchiii:~$ sudo startx
Password:
xauth:  creating new authority file /home/budha/.serverauth.6072


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux crunchiii 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 13 10:39:03 2007
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Module mach64 not found.
[drm] failed to load kernel module "mach64"
(EE) ATI(0): [dri] DRIScreenInit Failed
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

AUDIT: Fri Apr 13 10:58:06 2007: 6478 X: client 1 rejected from local host
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

++++++++++++++++++++++++++++++++++++++++++

This is a fresh install of Kubuntu and all I have done on the server is install the SSH server.

Pleaaaaaase tell me someone has had this problem before and has solved it!

---

### Post by finer recliner on 2007-04-13
you mention you're using putty. so i sassume you are trying to run linux stuff from a windows client? if so, you may need an app like Xwin32 to display X applications on windows.

---

### Post by finer recliner on 2007-04-13
if your client and server are both linux/unix based, this has worked for me when using SSH. this is in the default gnome terminal.

on client:
```

$ xhost + servername.domain.com
$ ssh -X username@servername.domain.com
//now connected to server
$ emacs &

```

---


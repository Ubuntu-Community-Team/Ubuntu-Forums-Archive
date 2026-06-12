---
title: "Cant find xorg.conf"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by micdhack on 2007-05-19
I need to find xorg.conf to enable touchpad but i cant find it. This file should be at /etc/X11/. 
Here is the list of files when i dir this folder:
[HTML]app-defaults             xinit                     Xresources
cursors                  xkb                       xserver
default-display-manager  xorg.conf.20070423040959  Xsession
fonts                    xorg.conf.20070423041102  Xsession.d
gdm                      xorg.conf.20070423041227  Xsession.options
rgb.txt                  xorg.conf.old             XvMCConfig
X                        xorg.conf.old~            Xwrapper.config
[/HTML]
Can anyone help me if there is a command that can point me to the right conf file?
Thanks in advance.

---

### Post by Najand on 2007-05-19
Type:
```
$ sudo updatedb
$ locate xorg.conf
``` to find it.

---

### Post by micdhack on 2007-05-19
```
micdhack@micdhack-laptop:~$ sudo updatedb
micdhack@micdhack-laptop:~$ locate xorg.conf
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster
/etc/X11/xorg.conf.20070423041102
/etc/X11/xorg.conf.20070423040959
/etc/X11/xorg.conf.old~
/etc/X11/xorg.conf.20070423041227
/etc/X11/xorg.conf.old
micdhack@micdhack-laptop:~$ 
```
Nope still cant find it!

---

### Post by Najand on 2007-05-19
Can you do a more specified ls:
```

$ ls -al /etc/X11

```

---

### Post by YoG%*@ on 2007-05-19
> **micdhack said:**
> ```
micdhack@micdhack-laptop:~$ sudo updatedb
micdhack@micdhack-laptop:~$ locate xorg.conf
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster
/etc/X11/xorg.conf.20070423041102
/etc/X11/xorg.conf.20070423040959
/etc/X11/xorg.conf.old~
/etc/X11/xorg.conf.20070423041227
/etc/X11/xorg.conf.old
micdhack@micdhack-laptop:~$ 
```
Nope still cant find it!

hi there!

well, you at least seem to have backups... (xorg.conf.old, etc...). what did you do before the file  went missing? did you edit / maybe accidentally delete it?

mux

---

### Post by lazyart on 2007-05-19
I wonder how you've even in the GUI without it.

You can copy one of the old ones:
```
cd /etc/X11
sudo cp xorg.conf.old xorg.conf
```You might have a problem with X starting on next reboot, in which case you'll have to log in at the command line and type ```
sudo dpkg-reconfigure xserver-xorg
```

Good luck!

---

### Post by micdhack on 2007-05-19
good idea i will try to reconfigure it. but it is strange. I though without xorg ubuntu wont start

by the way this is the coomand you asked for:
> micdhack@micdhack-laptop:~$ ls -al /etc/X11
total 120
drwxr-xr-x  10 root root  4096 2007-05-19 14:05 .
drwxr-xr-x 128 root root 12288 2007-05-19 20:07 ..
drwxr-xr-x   2 root root  4096 2007-04-15 15:00 app-defaults
drwxr-xr-x   2 root root  4096 2007-04-15 14:59 cursors
-rw-r--r--   1 root root    14 2007-04-15 15:01 default-display-manager
drwxr-xr-x   7 root root  4096 2007-04-23 14:31 fonts
lrwxrwxrwx   1 root root     6 2007-04-23 06:37 gdm -> ../gdm
-rw-r--r--   1 root root 17371 2007-02-13 12:02 rgb.txt
lrwxrwxrwx   1 root root    13 2007-04-23 06:37 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2007-04-15 14:54 xinit
drwxr-xr-x   2 root root  4096 2007-04-15 14:50 xkb
-rw-r--r--   1 root root  3586 2007-04-23 04:09 xorg.conf.20070423040959
-rw-r--r--   1 root root  4310 2007-04-23 04:11 xorg.conf.20070423041102
-rw-r--r--   1 root root  3900 2007-04-23 04:12 xorg.conf.20070423041227
-rw-r--r--   1 root root  4404 2007-05-19 14:05 xorg.conf.old
-rw-r--r--   1 root root  4349 2007-04-23 14:14 xorg.conf.old~
drwxr-xr-x   2 root root  4096 2007-04-15 14:50 Xresources
drwxr-xr-x   2 root root  4096 2007-04-15 14:59 xserver
-rwxr-xr-x   1 root root  3911 2006-08-07 22:01 Xsession
drwxr-xr-x   2 root root  4096 2007-04-23 19:46 Xsession.d
-rw-r--r--   1 root root   234 2006-08-07 22:01 Xsession.options
-rw-r--r--   1 root root    13 2006-09-12 06:44 XvMCConfig
-rw-------   1 root root   614 2007-04-15 14:50 Xwrapper.config


---

### Post by earobinson on 2007-05-19
Im pretty sure ubuntu will just take its best guess if it cant find a setting file. (for most settings files that is)

---

### Post by Najand on 2007-05-21
I think the xorg.conf.old is your lost xorg.conf.
Try to copy it as xorg.conf:
```

sudo cp xorg.conf.old xorg.conf

```
If you prefer to set it everything again, do this in a console:
```

sudo dpkg-reconfigure xserver-xorg

```
And it will make a new one for you, but you need to configure everything.

---


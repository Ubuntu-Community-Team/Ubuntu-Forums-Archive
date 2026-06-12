---
title: "Error after installing updates"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by dueY on 2006-08-13
Hello, it's been a while since I've posted here but I've been using Windows this summer.  I'm trying to get my Ubuntu back up to date and I have this annoying problem whenever I install updates.
```

Errors were encountered while processing:
 gaim
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So I tried this:
```

duey@what:~$ dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 gaim                 multi-protocol instant messaging client

duey@what:~$ sudo dpkg --configure -a
Setting up gaim (1.5.0+1.5.1cvs20051015-1ubuntu10) ...
rmdir: /usr/share/doc/gaim: Directory not empty
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gaim

```

This error doesn't appear to have any real negative effect on my system, but I do wish to fix it so I can stop seeing the annoying message and update my gaim. I don't remember how to fix this so I turn to you guys to help. Thanks in advance.

---

### Post by dueY on 2006-08-13
Just as a note I've tried to remove and reinstall it:
```

duey@what:~$ sudo aptitude remove gaim
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  gdk-imlib1 gnome-cups-manager python-netcdf totem
The following packages will be REMOVED:
  gaim
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 2200kB will be freed.
Writing extended state information... Done
(Reading database ... 136621 files and directories currently installed.)
Removing gaim ...
duey@what:~$ sudo aptitude install gaim
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  gdk-imlib1 gnome-cups-manager python-netcdf totem
The following NEW packages will be installed:
  gaim
0 packages upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 836kB of archives. After unpacking 2200kB will be used.
Writing extended state information... Done
Get:1 http://archive.ubuntu.com dapper/main gaim 1:1.5.0+1.5.1cvs20051015-1ubuntu10 [836kB]
Fetched 836kB in 3s (254kB/s)
Selecting previously deselected package gaim.
(Reading database ... 136589 files and directories currently installed.)
Unpacking gaim (from .../gaim_1%3a1.5.0+1.5.1cvs20051015-1ubuntu10_i386.deb) ...
Setting up gaim (1.5.0+1.5.1cvs20051015-1ubuntu10) ...
rmdir: /usr/share/doc/gaim: Directory not empty
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gaim
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gaim (1.5.0+1.5.1cvs20051015-1ubuntu10) ...
rmdir: /usr/share/doc/gaim: Directory not empty
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gaim

```

---

### Post by msak007 on 2006-08-13
When you try to uninstall gaim, try doing

```
sudo aptitude purge gaim
``` or 
```
sudo apt-get remove --purge gaim
``` instead to see if it'll remove any settings and documents left behind. If that doesn't work after you uninstall gaim, try to remove the non-empty doc directory as that seems to be where the problem was during the reinstall

```
sudo rm -r /usr/share/doc/gaim
``` 
Then try to update and install it again.

---

### Post by encompass on 2006-08-13
when you just remove the gaim program it leaves the settings there... I think the command is called "purge"
```
sudo apt-get --purge remove gaim
```
I would also try removing your gaim dir... if you don't care about it...
```
cd
rm -rf .gaim
```
did it help?

---


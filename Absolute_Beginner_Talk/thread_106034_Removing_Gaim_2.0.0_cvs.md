---
title: "Removing Gaim 2.0.0 cvs"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-19
I tried using the deb file from this post; [http://www.ubuntuforums.org/showthread.php?t=100899&highlight=gaim+beta](http://www.ubuntuforums.org/showthread.php?t=100899&highlight=gaim+beta)

darren@kubuntu:~/Desktop$ sudo apt-get remove gaim
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gaim
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 14.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 72566 files and directories currently installed.)
Removing gaim ...
dpkg - warning: while removing gaim, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing gaim, directory `/usr/local/lib' not empty so not removed.
dpkg - warning: while removing gaim, directory `/usr/local' not empty so not removed.

As you can see im trying to remove it, but it wont get rid of the gaim directories in those folders. Does anyone know why?

---

### Post by mztriz on 2005-12-19
I am having the same problems... I removed the CVS and I tried to install the beta version , with no luck. ```
root@ubuntu2:/home/mztriz# sudo alien /home/mztriz/Desktop/gaim2.0.0-0.beta1.fc4.i386.rpm
mkdir: cannot create directory `gaim-2.0.0': File exists
mkdir: cannot create directory `gaim-2.0.0/debian': File exists

```

---

### Post by mztriz on 2005-12-19
> **Rackerz]I tried using the deb file from this post said:**
> http://www.ubuntuforums.org/showthread.php?t=100899&highlight=gaim+beta[/url]

darren@kubuntu:~/Desktop$ sudo apt-get remove gaim
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gaim
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 14.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 72566 files and directories currently installed.)
Removing gaim ...
dpkg - warning: while removing gaim, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing gaim, directory `/usr/local/lib' not empty so not removed.
dpkg - warning: while removing gaim, directory `/usr/local' not empty so not removed.

As you can see im trying to remove it, but it wont get rid of the gaim directories in those folders. Does anyone know why?
I know what to do go to terminal and type in ```
gksudo nautilus
```
enter your root password if needed, then go to your home folder and delete the gaim-2.0.0 or whatever it's called folder lol. Then go ahead and install the version of gaim you wanted.

---

### Post by Rackerz on 2005-12-19
I'm still having trouble! I can't remove those directories or actually start up Gaim once it's installed.

---


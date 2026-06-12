---
title: "can't delete/uninstall a program through synaptic"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by halesquad on 2007-07-11
I have been trying to uninstall a program called oss-linux which i don't think that i need and it is not uninstalling in the usual way through the synaptic and i need another way to get rid of it please. 

Thank you 

Stephen

---

### Post by Majorix on 2007-07-11
```
sudo apt-get remove oss-linux
```

should do.

---

### Post by halesquad on 2007-07-11
```
stephen@stephen-desktop:~$ sudo apt-get remove oss-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tetex-base libsdl-gfx1.2-4 libkdegames1 libsdl-net1.2 libsdl-ttf2.0-0
  libgtk1.2-common libsdl-mixer1.2 tex-common libsmpeg0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  oss-linux
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7377kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 132168 files and directories currently installed.)
Removing oss-linux ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux (--remove):
 subprocess pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by sugarland2k on 2007-07-11
Ouch!  Try sudo apt-get autoremove.
This can help clean up problems with bad installations/removals...  


If this will not work, I noted the "Please resolve the situation and remove file"
"/usr/lib/oss/starting". Then start OSS by running "soundon" again.  <Not sure about this, hopefully autoremove will work>   Good luck!

---

### Post by halesquad on 2007-07-11
```
stephen@stephen-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tetex-base libsdl-gfx1.2-4 libkdegames1 libsdl-net1.2 libsdl-ttf2.0-0
  libgtk1.2-common libsdl-mixer1.2 tex-common libsmpeg0
The following packages will be REMOVED
  libgtk1.2-common libkdegames1 libsdl-gfx1.2-4 libsdl-mixer1.2 libsdl-net1.2
  libsdl-ttf2.0-0 libsmpeg0 tetex-base tex-common
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 82.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 132168 files and directories currently installed.)
Removing libgtk1.2-common ...
Removing libkdegames1 ...
Removing libsdl-gfx1.2-4 ...
Removing libsdl-mixer1.2 ...
Removing libsdl-net1.2 ...
Removing libsdl-ttf2.0-0 ...
Removing libsmpeg0 ...
Removing tetex-base ...
Removing tex-common ...
Setting up oss-linux (v4.0-1002) ...
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error processing oss-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Majorix on 2007-07-11
> Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.

If it says that, it must know something. Do as it says and remove that file:
```
sudo rm /usr/lib/oss/starting
```

And once done you can try uninstalling it again. I believe if the problem is fixed by then, Synaptic will also be able to remove it. If not, do it in terminal and paste the log here.

Good luck!

---

### Post by halesquad on 2007-07-11
this is what i did after removing the sudo rm /usr/lib/oss/starting 

```
stephen@stephen-desktop:~$ sudo apt-get remove oss-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  oss-linux
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7377kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125757 files and directories currently installed.)
Removing oss-linux ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux (--remove):
 subprocess pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 31: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 33: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 35: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 41: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 41: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 48: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 oss-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by halesquad on 2007-07-12
bump

---

### Post by Seisen on 2007-07-12
Go into synaptic and then click on edit the select fix broken packages and then try uninstalling it and see what happens.

---

### Post by Al3xK3aton on 2007-07-12
If you reformat your hard drive, this program will be completely uninstalled. You'll have to reinstall everything else, but you've already done it in the past, judging by the fact that you have it installed currently, so I won't explain how to reinstall linux again.

---

### Post by halesquad on 2007-07-12
> Go into synaptic and then click on edit the select fix broken packages and then try uninstalling it and see what happens.

I tryed the above and i encounted the same problems as before that it brings up an error message i.e. it didn't remove it

---


---
title: "What is this error?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by aeonwings on 2008-03-22
I'm trying to fix a couple of broken dependencies, and it's giving me the following error - anyone have any idea?

[[IMG]http://img214.imageshack.us/img214/9832/screenshotar5.th.png[/IMG]](http://img214.imageshack.us/my.php?image=screenshotar5.png)

And these are the broken dependencies....

[[IMG]http://img143.imageshack.us/img143/5664/screenshot1jk8.th.png[/IMG]](http://img143.imageshack.us/my.php?image=screenshot1jk8.png)

---

### Post by Infinite Recursion on 2008-03-22
Not entirely certain how to fix this with the frontend, as I don't use it myself, but you may be able to do so using the fix-dependencies function of apt-get:
```
sudo apt-get install -f
```

---

### Post by lavinog on 2008-03-23
Please change the title to something meaningful like: dependency error in synaptic
This helps you and future users that have the same problem.

---

### Post by aeonwings on 2008-03-23
> **Infinite Recursion said:**
> Not entirely certain how to fix this with the frontend, as I don't use it myself, but you may be able to do so using the fix-dependencies function of apt-get:
```
sudo apt-get install -f
```

This is what I got when I tried to use that code.....
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libevas0-loaders-all libecore0-x libevas-engine-software-x11 libecore0-txt
  libevas-loader-png libevas-saver-png libevas-loader-svg
  libevas0-engine-software-x11 libevas-loader-tiff libevas0-loader-eet
  libevas-loader-xpm libevas0-loader-gif libevas0-engine-software-generic
  libevas0-loader-png libevas0-loader-svg libevas-saver-jpeg
  libevas0-loader-xpm libevas0-loader-tiff libecore0-imf-evas giblib1
  libevas0-saver-eet libecore0-file libembryo0-bin libecore0-fb
  libevas0-engine-buffer libevas0-saver-jpeg libecore0-evas libxine1-gnome
  libevas0-saver-png libevas-loaders-all libevas-engine-software-generic
  libecore0-bin libecore0-con scrot libedje0-bin libecore0-imf libecore0-ipc
  libecore0-job libevas0-loader-jpeg libefreet1 libevas-loader-eet
  libecore0-config libevas-loader-gif libevas-saver-eet
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libevas-engines
The following NEW packages will be installed:
  libevas-engines
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
29 not fully installed or removed.
Need to get 0B/48.7kB of archives.
After unpacking 201kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 120131 files and directories currently installed.)
Unpacking libevas-engines (from .../libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/evas/modules/engines/buffer/linux-gnu-i486/module.so', which is also in package libevas0-engine-buffer
Errors were encountered while processing:
 /var/cache/apt/archives/libevas-engines_0.9.9.042+cvs20080309-0gutsy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---


---
title: "Synaptic Broken"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by whoosh on 2007-09-08
I tried installing kubuntu-desktop through synaptic so I could use amarok.  But one of the required depedencies is messed up and I keep getting the error:

```
E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
```

I tried ```
sudo rm /usr/lib/libmjpegutils-1.8.so.0.0.0
``` and reinstalling but it's not working.  Anyone have any ideas?

---

### Post by diatribe on 2007-09-08
you could try sudo apt-get install -f

also, I think you could have installed amarok without installing kubuntu-desktop

---

### Post by Xorg.conF on 2007-09-08
Yea diatribe is right you don't need the KDE desktop environment, and theres even a version of amarok for Ubuntu called exaile, you can use apt-get to get it.

---

### Post by whoosh on 2007-09-08
When I attempt to do sudo apt-get install -f, I get the error message ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmjpegtools0c2a
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmjpegtools0
The following NEW packages will be installed:
  libmjpegtools0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

When I do sudo apt-get autoremove, it tells me ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  transcode: Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installed
E: Unmet dependencies. Try using -f.

```

Any ideas?

---

### Post by diatribe on 2007-09-08
make sure synaptic is not running (or any other package manager), then from terminal type

sudo rm /var/cache/apt/archives/lock
sudo apt-get install -f

then you can run sudo apt-get autoremove

---

### Post by whoosh on 2007-09-08
Still not working, i'm getting the same error as before.  When I run sudo apt-get install -f, I get ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmjpegtools0c2a
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmjpegtools0
The following NEW packages will be installed:
  libmjpegtools0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 209kB of archives.
After unpacking 537kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libmjpegtools0
Install these packages without verification [y/N]? y
Get:1 http://www.debian-multimedia.org stable/main libmjpegtools0 1:1.8.0-0.4 [209kB]
Fetched 209kB in 2s (103kB/s)          
(Reading database ... 147145 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I do sudo apt-get autoremove, it tells me to use sudo apt-get -f install ;/

---

### Post by diatribe on 2007-09-08
the problem is a dependency conflict but I am unsure of how to resolve it.  try going into synaptic and removing libmjpegtools0c2a maybe?

---

### Post by schorsch on 2007-09-08
You are trying to install "libmjpegtools0" from some debian repos ..... and it isn't a good idea to mix debian and ubuntu packages! Why won't you use the package "libmjpegtools0c2a" from the ubuntu repos any longer? Why not install "amarok" via synaptic??

---

### Post by whoosh on 2007-09-08
Well, I did that before I did sudo apt-get install -f and I got the same error... blah stupid kubuntu desktop

---

### Post by schorsch on 2007-09-08
```
gksu gedit /etc/apt/sources.list
```
and put a # in front of every line that has a debian in it.
Then
```
sudo apt-get update
sudo apt-get install amarok
```

---

### Post by whoosh on 2007-09-08
There was already a thread about this...woops.  I fixed it by doing this

[http://ubuntuforums.org/showthread.php?t=479133&highlight=libmjpegtools0c2a](http://ubuntuforums.org/showthread.php?t=479133&highlight=libmjpegtools0c2a)..

I can install amarok...but I can't load songs on.  I was told that it would work if I installed kubuntu desktop first...

---

### Post by schorsch on 2007-09-08
Amarok works just fine without the meta package kubuntu-desktop installed on Gnome. What is your problem now?

---


---
title: "Problem installing XFCE in terminal"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-09-26
I just downloaded the .bin file for the XFCE desktop and ran chmod a+x then ran it. It looked like it was going to work perfectly until...
```
charlie@charlie-desktop:~$ cd Desktop
charlie@charlie-desktop:~/Desktop$ chmod a+x xfce4-4.2.3.2-installer.bin charlie@charlie-desktop:~/Desktop$ ./xfce4-4.2.3.2-installer.bin
Verifying file integrity... OK.
Extracting the installer... OK.
Checking for usable C compiler... gcc
Checking for usable C++ compiler... g++
Checking for GNU make... GNUmake
Checking for package config tool... pkg-config
Checking for GLib (GModule) >= 2.2.0... not found, see /home/charlie/.xfce4.installer-log for details
Cleaning up... OK.
charlie@charlie-desktop:~/Desktop$

```
Then I logged out and tried to start XFCE but it wasn't there. What happened? I have a feeliong it had something to do with
```
Checking for GLib (GModule) >= 2.2.0... not found, see /home/charlie/.xfce4.installer-log for details
```
Unfortunately, I couldn't find that log file.
Any suggestions on how to get this to work?

---

### Post by whizbaby on 2006-09-26
xfce wasn't installed, the installer only checked your environment.
You will have to get and install a newer version of*libglib2.0-0* (libglib2.2-0 or so)and try again.

---

### Post by Crazy Man on 2006-09-26
Try this:

```
$ sudo apt-get install xubuntu-desktop

```

You could also do:

```
$ sudo apt-get install xfce4

```

Might want to look up where to get the newest version though (preferably as a .deb to save you some hassle).

---

### Post by aysiu on 2006-09-26
Do you not have an internet connection on your computer? The easiest way to install XFCE is this: ```
sudo aptitude update
sudo aptitude install xfce4
``` If you want the Ubuntu-specific version, you can do this: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by whizbaby on 2006-09-26
Oh, I misunderstood the post, it says xfce4-4.2 and not xfce 4.4, so the other guys are right and you don't need to use the installer (unless you want version 4.4).

---

### Post by mongooseman1128 on 2006-09-27
but doesn't the line about Glib >= 2.2.0 mean I need a new version of Glib? Because I checked in synaptic and I think I only have 2.0.0.

---

### Post by whizbaby on 2006-09-27
No this only means that the installer needs a newer version to build xfce on your computer. You seem to want the official release version of xfce (4.2.3...), so why not installing it the way it's meant to be(apt-get, aptitude or synaptic)? You ONLY need to install manually if you want the latest BETA of xfce (4.3.99.1, release candidate for 4.4), and even for that you can find .deb packages so you don't need to mess around.

---

### Post by mongooseman1128 on 2006-09-28
okay I've gotcha. thanks.

---


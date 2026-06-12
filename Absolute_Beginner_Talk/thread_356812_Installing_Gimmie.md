---
title: "Installing Gimmie"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by flawed_singularity on 2007-02-08
Hi 
I am very new to ubuntu. I am attempting to install Gimmie and running this command however apt-get install will not install the python-gnome2-desktop-dev portion. All the others are fine. Any ideas appreciated:( 

apt-get install python2.4 python2.4-dev python-gnome2-dev python-gnome2-desktop-dev libgnomecups1.0-dev
Reading package lists... Done
Building dependency tree... Done
python2.4 is already the newest version.
python2.4-dev is already the newest version.
python-gnome2-dev is already the newest version.
E: Couldn't find package python-gnome2-desktop-dev

---

### Post by taurus on 2007-02-08
I have package python-gnome2-desktop-dev on my Search using synaptic!  Did you remember to enable both universe & multiverse in /etc/apt/sources.list by removing the # in front of all the lines with deb at the beginning?

```
gksudo gedit /etc/apt/sources.list
```
Then

```
sudo apt-get update
sudo apt-get install python-gnome2-desktop-dev
```

---

### Post by flawed_singularity on 2007-02-08
Thanks for the reply. I have uncommented thos entries in the sources.list file and ran apt-get update but still get the same message. You mentioned synaptic in your file. What is the url for that?

---

### Post by airtonix on 2007-03-25
synaptic is a program found under the main menus.

System -> Administration -> Synaptic Package Manager

---

### Post by eljalill on 2007-03-25
Just a note to you:
Gimmie is still quite buggy, it crashes frequentely (around 4or 5 times a day for me), and new fixes come out pretty often. If you say, you are still new, you might want to wait, until it is more stable....

---


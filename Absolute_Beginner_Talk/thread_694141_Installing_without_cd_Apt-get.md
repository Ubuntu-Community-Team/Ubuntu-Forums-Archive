---
title: "Installing without cd? Apt-get"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by ryana on 2008-02-11
I'm trying to install a few things but have a problem. I'm using Ubuntu 6.06.1, but when I try to install anything I get the message:

Need to get 0B/3942kB of archives.
After unpacking 13.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)'
in the drive '/cdrom/' and press enter

This typically wouldn't be a problem except that I have misplaced the disc.
Can I get around this? I don't really want to download and burn a new image.

---

### Post by taurus on 2008-02-11
Open a terminal and edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, make sure you remove the # in front of all the lines that start with **deb** & **deb-scr**.  Save it and run

```
sudo apt-get update
```
Now, it won't ask you to insert the CD-ROM again every time you want to install something.  It will try to pull it down from the net.

---

### Post by ryana on 2008-02-11
Thank you so much!

---


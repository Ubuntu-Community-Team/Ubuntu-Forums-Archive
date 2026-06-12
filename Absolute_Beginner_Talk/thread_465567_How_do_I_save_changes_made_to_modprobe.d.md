---
title: "How do I save changes made to modprobe.d?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by GregoryMA on 2007-06-05
I am going through the process of installing ndiswrapper as described at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29) however I have to disable the bcm43xx driver so that it doesn't cause problems for ndiswrapper when I install the windows driver.  However, when I try to save the changes I made to modprobe.d I can't because it is read-only.  How do I add the 'blacklist bcm43xx' command to this file?
Thanks, Greg.

---

### Post by Nekiruhs on 2007-06-05
```
gksudo gedit /path/to/modprobe.d
```
if your on Ubuntu
```
kdesu kate /path/to/modprobe.d
```
for Kubuntu

---

### Post by kevdog on 2007-06-05
Is there a difference if you type

sudo gedit /path/to/modprobe.d

versus

gksudo gedit /path/to/modprobe.d

---

### Post by Nekiruhs on 2007-06-05
> **kevdog said:**
> Is there a difference if you type

sudo gedit /path/to/modprobe.d

versus

gksudo gedit /path/to/modprobe.d
Yes, gksudo is for graphical applications. Bad things can happen if you use sudo with a graphical application. For instance,  sudo gedit screwed up something in my sudoers file and I lost sudo priveleges. Since I didn't have sudo I couldn't edit the sudoers file. I had to go into recovery mode to fix it. This probably won't happen to you, but just use  gksudo for GNOME, and kdesu for KDE.

---

### Post by kevdog on 2007-06-05
Hate to keep nagging but what is a sudoers file??

---

### Post by GregoryMA on 2007-06-06
That worked.  Thanks for the advice!

---


---
title: "Can you use Synaptic to install downloaded .deb software"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-09-15
Hi, Guys!

I had a bit of a play, but can't figure out if you can use Synaptic package manager to install downloaded .deb packages from your local HDD.
Is it possible?
I'd rather do that than using a command line.

Regards,
Roger

---

### Post by Kilz on 2006-09-16
> **ramjet_1953 said:**
> Hi, Guys!

I had a bit of a play, but can't figure out if you can use Synaptic package manager to install downloaded .deb packages from your local HDD.
Is it possible?
I'd rather do that than using a command line.

Regards,
Roger

Double click on the deb file. Gdebi should start and install it. But the command line is your friend. If you have a lot of files you could put them on your desktop. Open a terminal, type in ```
cd ~/Desktop
``` then ```
sudo dpkg -i *.deb
``` and install them all at once. Instead of double clicking and instaling them one at a time.
Also you might want to [look at and save this page]("http://www.monkeyblog.org/ubuntu/installing/") its full of a lot of good information about installing things.

---

### Post by aysiu on 2006-09-16
Close. There's a program called *gdebi* that allows you to double-click-install .deb files.

Honestly, though, the command-line isn't that scary. Let's say you have a few .deb files on your desktop. You just paste in these two commands and they're all installed: ```
cd ~/Desktop
``` This **c**hanges **d**irectories to the **Desktop** directory. ```
sudo dpkg -i *.deb
``` which installs (dpkg) all (*) .deb files with root privileges (sudo).

---

### Post by ramcosca on 2006-09-16
Heh, both explained the same thing. Both are great teachers. Thanks to both.

---


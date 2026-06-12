---
title: "Re-installing Ubuntu"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-09-18
I wonder should I reinstall Ubuntu?  I originally installed it some weeks ago and then added KDE which I removed later using the command line.  I then reinstalled it and since have Xubuntu shown on screen as I bootup and log off.  The system is working fine, but I seem to have a number of programs I didn't expect to see and will probably never use.  I am now slightly confused about what exactly I'm running on my machine and I'm having thoughts about re-installing everything from scratch again.  Before I do can I ask if there is a way around this, without having to re-install everything?

---

### Post by alecjw on 2006-09-18
I'm not sure if this will work but try sudo aptitude remove ubuntu-desktop
then:
sudo aptitude install ubuntu-desktop
in the terminal. That might get your login screen back.

---

### Post by Mark_in_Hollywood on 2006-09-18
Try using

apt-get --remove [filename-executable]

or better still, use

aptitude

which will carefully remove programs, but qualify dependencies.

Yet, reading your post, I say: less is more

---

### Post by bulldog on 2006-09-18
You could use Alacarte to get rid of all the apps you don't want to see.

They are not uninstalled,only not visible,so you have a clearer look at your menu's.

---

### Post by ncappel1 on 2006-09-18
Here's a great page that explains very clearly how to install ubuntu with a separate /home partition (where all of your personal files are stored).
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

By using this method you can reinstall ubuntu or upgrade in the future without risking (at least not very much :p) the loss of your data. 
(you obviously want to skip the steps related to making partitions for a windows system, unless you want to do that!)

---

### Post by a.v.l on 2006-09-20
Thanks guys.

---


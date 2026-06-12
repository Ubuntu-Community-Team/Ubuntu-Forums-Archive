---
title: "kde 4.0 install on ubuntu 7.10 server"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by wasing on 2008-03-17
i normally use kubuntu but my dad's business requires allot of backups so i decided to make a samba server (Ubuntu Server 7.10) on one of my empty partitions (200GB) each backup is around 2GB.
 
Should i install KDE because im not even sure how to use the command line im very basic with it. or should i just try and set up a samba on my kubuntu and make a seperate partition for my dad's backups thanks. also i could learn to use the command line.

btw im not for sure but i thought to get the kubuntu GUI you had to do 

Sudo apt-get kde-desktop

kdm

but i have no idea thanks for your time

---

### Post by amingv on 2008-03-18
While you could install KDE4 to your server (one way or another), it is not advisable for a server platform due to possible unstability issues (a server should be kept as stable as possible). If you want to install KDE then I suggest you install 3.5, until 4 gets more robust:

```
sudo apt-get install kubuntu-desktop
```

If you'll allow a suggestion, some will recommend a lighter setting for a server (like XFCE):

```
sudo apt-get install xubuntu-desktop
```

Finally, you don't need to be an ace at the CLI to manage a home/small office server, in fact, you'll just set it up the first time and let it be (or manage it remotely), so if you're interested in the CLI, this may be a place to start:
[http://linuxcommand.org/](http://linuxcommand.org/)

Have fun.

---


---
title: "Problem reinstalling ALSA drivers.  Help?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by DayOldPorridge on 2008-01-25
I just installed Gutsy Gibbon yesterday, so I´m totally new to Linux.  Anyway, my microphone wasn´t working, so I tried reinstalling the drivers to see if that would fix the problem.

Here´s what I did:

> ~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
[sudo] password for dominique:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  alsa-base* alsa-utils* fast-user-switch-applet* gdm* linux-sound-base*
  ubuntu-desktop* ubuntu-minimal*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 20.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 88947 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing alsa-base ...
Purging configuration files for alsa-base ...
Remaking /dev/sndstat.
Removing ubuntu-desktop ...
Removing fast-user-switch-applet ...
Purging configuration files for fast-user-switch-applet ...
Removing gdm ...
Purging configuration files for gdm ...
Removing user `gdm' ...
Done.
dpkg - warning: while removing gdm, directory `/usr/share/gdm/applications' not empty so not removed.
Removing alsa-utils ...
Purging configuration files for alsa-utils ...
Removing linux-sound-base ...
Purging configuration files for linux-sound-base ...
dominique@ze-zipaktli:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-sound-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-sound-base has no installation candidate
dominique@ze-zipaktli:~$ sudo apt-get install gdm ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gdm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gdm has no installation candidate

Any advice?

---

### Post by DayOldPorridge on 2008-01-25
Bump?  :]

---

### Post by jlambeth1 on 2008-01-25
I have tried the following steps to get my sound working that I found in another post.  I don't know what kind of system you have but it worked for my Dell Latitude D630 laptop.  But one thing to keep in mind is that I followed these steps right after a new installation.  Previously I tried a combination of solutions before trying the ones below and had no luck.  So you might want to reinstall gutsy and then try these steps.  Hope this helps.

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

---

### Post by stchman on 2008-01-25
> **DayOldPorridge said:**
> I just installed Gutsy Gibbon yesterday, so I´m totally new to Linux.  Anyway, my microphone wasn´t working, so I tried reinstalling the drivers to see if that would fix the problem.

Here´s what I did:



Any advice?

I have a script that installs the ALSA drivers for the Intel ICH7 soundcards.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

---

### Post by DayOldPorridge on 2008-01-29
Thanks for the help!  Although eventually I just ended up re-installing Gutsy, which fixed the soundcard thing as well as a few other problems and errors that kept popping up, so now it's all good.  Thanks, though.  :D  Might be helpful for future users.

---


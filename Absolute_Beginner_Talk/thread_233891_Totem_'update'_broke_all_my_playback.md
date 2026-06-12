---
title: "Totem 'update' broke all my playback"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by bsmith1051 on 2006-08-10
I had been happily using Totem Movie Player to watch DVDs and DivX files until last week.  I was told that there was an update for Totem which required that something else be uninstalled.  I told it to go ahead and Totem was still there afterwards, but now it won't play anything.  From searching the forums here, it appears that the "update" switched from Totem-xine to Totem-gstreamer?  I found a package in Synaptic called "gstreamer0.10-ffmpeg" which said it included all sorts of codecs, but after installing it Totem still doesn't recognize DVDs.

Why was this update rolled-out if it was going to reset all your codec support?  The program doesn't look any different and I wasn't having any problems with the previous version.

---

### Post by Fass on 2006-08-10
Check your /etc/apt/sources.list file and make sure that the "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates" line is not just followed by "main restricted" but also by "universe multiverse". It should end up looking something like:

```
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
```

Do the same to the dapper-security ones. Then run

```
sudo aptitude update
```

Now, you can install a totem-xine package that works with the latest totem version (1.4.3).

---

### Post by Arisna on 2006-08-10
I had this problem, too.  All I had to do was run "sudo aptitude install totem-xine", accept the solution to downgrade totem to a version matching the current xine build, and go back to using the xine version, which I prefer.  Then, I used Synaptic to lock the version on totem to prevent the update from causing further issues.

---

### Post by Fass on 2006-08-10
> **Arisna said:**
> I had this problem, too.  All I had to do was run "sudo aptitude install totem-xine", accept the solution to downgrade totem to a version matching the current xine build, and go back to using the xine version, which I prefer.  Then, I used Synaptic to lock the version on totem to prevent the update from causing further issues.

There is a new totem-xine version that matches the totem version in the dapper-updates repository. No need to downgrade and lock.

---

### Post by bsmith1051 on 2006-08-10
Can you have both the -Xine and -gstreamer backends installed?  What was the reason for replacing the former with the latter?  If all the development (and future updates!) are going to be with gstreamer, I'm fine with sticking to that.  I just want my stuff to play in the meantime.

P.S.  I finally found the "gstreamer-fluendo-mpegdemux" package and that seems to have done the trick.  I just don't understand why I had to essentially start from scratch after an "update".

---

### Post by Fass on 2006-08-10
No, you can't have totem-xine and totem-gstreamer at the same time - that's why the update had to remove totem-xine to install totem-gstreamer. You were probably missing the "universe and multiverse" in the dapper-updates line and it couldn't find the latest version of totem-xine.

---

### Post by bsmith1051 on 2006-08-10
> **Fass said:**
> You were probably missing the "universe and multiverse" in the dapper-updates line and it couldn't find the latest version of totem-xine.
Yep, I think you were right.  I added those two.

Why does this have to be so complicated???

---

### Post by TFX360 on 2006-08-10
Like all frigging problems, money, most probably it can't be installed under official GNU license.

---

### Post by lime4x4 on 2006-08-10
well i did what was suggested here for the apt.lists but it's not working for me either. Totem currently isn't installed so when i try to install totem this is what i get

john@ubuntu:~$ sudo apt-get install totem
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  totem-gstreamer
Recommended packages:
  totem-gstreamer-firefox-plugin
The following packages will be REMOVED:
  totem-xine totem-xine-firefox-plugin
The following NEW packages will be installed:
  totem totem-gstreamer
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/1072kB of archives.
After unpacking 2773kB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by TFX360 on 2006-08-10
I assume you mean sources.list and not apt.list. I'll show you mine (it works)

```
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe universe multiverse

```

I left compiz out of the list, as it is for my Xgl/Compiz install.


Hope it helps,


TFX

---

### Post by Arisna on 2006-08-10
> **Fass said:**
> There is a new totem-xine version that matches the totem version in the dapper-updates repository. No need to downgrade and lock.
Er... I thought I had all of that stuff enabled already, and I hadn't seen your post when I posted.  You're right, though, and that works much better for me.  Thanks!

---


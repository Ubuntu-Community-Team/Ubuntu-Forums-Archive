---
title: "[SOLVED] Can't install kiba-dock"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by watnazn on 2007-12-30
Hey, I was wondering if anyone knows how to help me install kiba-dock. When i type in the second step in the terminal i get
```
desktop:~$ sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package automake1.9 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package automake1.9 has no installation candidate
```
And then i enter the next two codes when i get to 
```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru
```
and i get
```
desktop:~/kiba-dock$ svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru
The program 'svn' is currently not installed.  You can install it by typing:
sudo apt-get install subversion
bash: svn: command not found

```
And pretty much the same for the next steps.
I was wondering if anyone knows what to do, because i had kiba-dock before, and i used the same manual [HTML]http://ubuntuforums.org/showthread.php?t=554127[/HTML] and it worked.
Thanks Everyone.

---

### Post by Perfect Storm on 2007-12-30
Loooks like you havn't set up your sourcelist.

please post this;
```
cat /etc/apt/sources.list
```

---

### Post by watnazn on 2007-12-30
```
-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy restricted universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by Perfect Storm on 2007-12-30
As you can see all of your sources have been disable.
Go to System tab ---> administration ---> System Sources . Here you can enable everything  (remember to select sources as well).

To manually edit the sourcelist;
```
sudo nano /etc/apt/sources.list
```

[ctrl]+[o]=save
[ctrl]+[x]=exit


If you want to build a new sourcelist: 
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by watnazn on 2007-12-30
Thanks. you helped alot.

---


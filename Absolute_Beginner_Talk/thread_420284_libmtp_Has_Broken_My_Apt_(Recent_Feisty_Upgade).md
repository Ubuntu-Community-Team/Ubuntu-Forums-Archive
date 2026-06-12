---
title: "libmtp Has Broken My Apt (Recent Feisty Upgade)"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-04-23
I recently upgraded to Feisty. It gave me an error when I upgraded (I don't remember exactly...it was very vague), but everything seems to be alright, except for Apt. It says that my amarok is broken, and it looks like it's because of libmtp. Here are some relevant outputs (sorry for how long this is):

> tony@ubuntu-desktop:~$ **sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python2.4-dev libgtkxmhtml1 libcapplet1 libdbus-glib-1-dev libpq4 libzvt2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmtp5
The following NEW packages will be installed:
  libmtp5
0 upgraded, 1 newly installed, 0 to remove and 555 not upgraded.
2 not fully installed or removed.
Need to get 0B/92.7kB of archives.
After unpacking 319kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 186125 files and directories currently installed.)
Unpacking libmtp5 (from .../libmtp5_0.1.3-0ubuntu2_i386.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/libmtp5_0.1.3-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mtp-albumart', which is also in package libmtp
dpkg-deb: subprocess paste killed by signal (Broken pipe)[/B]
Errors were encountered while processing:
 /var/cache/apt/archives/libmtp5_0.1.3-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

> tony@ubuntu-desktop:~$ **sudo apt-get remove libmtp **
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
**  amarok: Depends: libmtp5 (>= 0.1.3) but it is not going to be installed**
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

> tony@ubuntu-desktop:~$ **sudo apt-get remove amarok**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
[B]  amarok-xine: Depends: amarok (= 2:1.4.5-0ubuntu7) but it is not going to be installed
               Depends: amarok but it is not going to be installed
[/B]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Here are the third-party repos in my sources.list:

> ## Quasi-Stable Beryl:
## 	deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

## SVN Beryl:
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

## MusicBrainz
# deb [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) edgy musicbrainz

## SwiftFox
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

## Exaile SVN
# deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy exaile-svn

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse
#AUTOMATIX REPOS END

Any idea where to go from here?

---

### Post by tonyr1988 on 2007-04-23
It looks like I've got it fixed. Here's what the problem was (just in case someone happens to have similar issues):

I had compiled libmtp from source in the past (needed a newer version). The libmtp that it wanted to install from the repos (because of amarok) had some files conflict with my old libmtp. It also wouldn't let me remove the old libmtp (what I wanted to do the whole time) because of the conflict (kinda dumb, if you ask me :P). I realized I could do this:

> sudo dpkg -r libmtp

And now everything seems to be working alright. Sorry for the forum clutter!

---

### Post by willo8allthepies on 2007-06-08
You are my hero, now getting on for 1 am and had been trying to figure this out for some hours now!

Cheers

---


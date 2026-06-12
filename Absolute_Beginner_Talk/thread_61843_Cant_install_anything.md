---
title: "Cant install anything"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by duke_nukem_time on 2005-09-02
For starters, the unofficialubuntu 5.0.4 starter guide is no help when installing programs from the linux disc. I found people trying to get complete noobs to use it, yet the latest AMD64 Ubuntu version doesn't the programs packaged. I keep gettting errors that the package isn't found.

Next, when I try to install Java JRE 5.0.4, it gives me this error:

Do you agree to the above license terms? [yes or no]
y
Unpacking...
Checksumming...
0
0
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_04-linux-i586.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

what is alien and how do I use it?

Third, i enabled multiverse repositories, yet I still get an error when running this in terminal:

E: Couldn't find package mplayer

It builds dependencies and repositories, but it can't find it. I did a google search for the package and still couldn't find it anywhere.

---

### Post by KingBahamut on 2005-09-02
Use the -- [http://ubuntuguide.org/](http://ubuntuguide.org/) -- entry for installing JRE. 

Be sure you also have all the repositories set right.

---

### Post by dbcoder on 2005-09-02
Alright, sounds like a misconfiguration.

Please overwrite your /etc/apt/sources.list with

```

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

type:
apt-get update

And then apt-get install sun-j2re1.5

And you are on your way to java goodness.

The problem you were encountering could have been 1.) trying to access the backports when it was completely messed up :P, or 2.) not having backports enabled.

Anyway, you should be good to go now.

---


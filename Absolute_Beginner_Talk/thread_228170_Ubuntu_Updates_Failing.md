---
title: "Ubuntu Updates Failing"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by dpaint4 on 2006-08-02
The automatic update system has several things in it that it can't download or can't update for some reason or another.

Should I care?

The little update icons is displayed constantly.

This is all because I wanted something from a private Dapper repository. The install that I wanted went well and I have the application that I was after, but now the result is a messed up update system.

If I remove the repository, all the stuff that came from there will be suddenly 'broken' right? This is something I kind of hate. You want one little thing but it has all this other stuff tied to it.

What can I do to make my update system normal again?

---

### Post by metalcoat on 2006-08-02
Please post the contents of your /etc/apt/sources.list
And could you specify what you mean by private repository

---

### Post by dpaint4 on 2006-08-02
Sure. It was [Asher256's Repository]("http://asher256-repository.tuxfamily.org/english.php"). An English/French repository maintained by an individual. I installed Gnormalize because it's a good gnome program for transcoding audio files, and I have a large FLAC library that I like to transcode to lossy formats for portables.

This is the only non-standard repository that I've added to my list, aside from the Universe and Multiverse repositories.

Here's my sources.list:

> deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## Asher256's Repository
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french


---

### Post by dpaint4 on 2006-08-02
I should have noticed the error message more carefully. It instructed me to open the package manager and do a 'Mark all Upgrades' which repared whatever needed to be repared, and now my updates are functioning normally again and my system is happy.

Sorry to have bothered you. I'm not exactly used to error messages being accurate or informative. I should have expected as much from Ubuntu, the world's most fabulous OS.

---


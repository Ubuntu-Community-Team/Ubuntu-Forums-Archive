---
title: "msttcorefonts install problem (I think this is an easy one)"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-08-09
Hey, Group-

I just re-installed Ubuntu after some experiments of mine went awry and I was over my head... so as part of my starting over, I'm trying to re-install msttcorefonts.

Here's what I did, and what it said:

~$ sudo apt-get install msttcorefonts
Password:
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

This is actually the second time I tried, and the first time around, the messages were similar, but slightly different.

I believe I've correctly enabled Universe and Multiverse repositories in sources.list, but here it is just in case:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Have I done everything correctly so far?

Thanks for any help you may have!

-Mark

---

### Post by frenkel on 2006-08-09
You need to enable multiverse by adding these two lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse

---

### Post by mjpatey on 2006-08-09
Thank you!  I thought that was covered by the uncommenting; it's a little confusing the way they word it in the commented instructions.

I'll give that a shot, retry, and post my results!

-Mark

---

### Post by mjpatey on 2006-08-09
Hmm... I get the same results.  Here's what happened:

~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

It just occurred to me... after enabling the multiverse, should I have rebooted?

-Mark

---

### Post by Jagot on 2006-08-09
> **mjpatey said:**
> It just occurred to me... after enabling the multiverse, should I have rebooted?

No, but you do need to update the cache of files in the repo's stored on your computer, so you would do:

```
sudo aptitude update
sudo aptitude install msttcorefonts
```

Failing that, replace the contents of your sources.list with this one:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Then do the same.

---

### Post by mjpatey on 2006-08-09
Beautiful!  Thanks, Jagot.  I knew it was something small and simple, just didn't know what.

That worked perfectly for me without needing to replace my sources.list.

-Mark

---


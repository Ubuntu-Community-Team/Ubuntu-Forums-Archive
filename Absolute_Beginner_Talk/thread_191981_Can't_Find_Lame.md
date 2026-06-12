---
title: "Can't Find Lame"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Farthing-or-less on 2006-06-08
Trying to install MP3 ripping support, but can't find lame using synaptic. All repositories are enabled. I tried downloading one of the gstreamer-ugly-m, and got a no-can-install message because there liblame is not out there either.

No problems getting these things when using breezy. Where can they be found now???

Thanks

---

### Post by mjm115 on 2006-06-08
Are you sure that you have the 'multiverse' repository enabled?  Lame is located there.  I had no problems installing it.  What does your sources.list file look like?

---

### Post by Farthing-or-less on 2006-06-08
It was, but you're still right. The repository was enabled, but I went through and disabled and then re-abled them, and then the files appeared. Odd.

Thanks

---

### Post by darkdigger on 2006-06-08
I'm having the exact same problem. I try to install gstream-0.10-plugins-ugly-multiverse and it says there are unresolvable dependencies:

```
gstreamer0.10-plugins-ugly-multiverse:
 Depends: liblame0 (>=3.96.1-1) but it is not installable
```

I've tried reloading all my repositories many times. I even tried deselecting, reloading, selecting and then reloading them again like farthing did. Here's my sources.list

```
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

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
```

If anybody could help that'd be great. BTW, this happens on both my computers that are running 6.06.

-Arash

---

### Post by christhemonkey on 2006-06-08
Try changing the repositries from the [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) to just [http://archive.ubuntu.com](http://archive.ubuntu.com)

The us archive may not have properly mirrored the main one yet.


Edit: You dont have multiverse enable.... just backports.
Add
```
deb http://archive.ubuntu.com dapper multiverse
```

---

### Post by darkdigger on 2006-06-08
Thanks christhemonkey. I indeed didn't have multiverse enabled. So what's the difference between the backports and regular repository? and why isn't the regular multiverse repository placed in the sources.list by default (even if it's just disabled)?

Also, to anyone who needs to add that line to their sources.list it should be as follows:

```
deb http://archive.ubuntu.com/ubuntu/ dapper multiverse
```

-Arash

---

### Post by christhemonkey on 2006-06-08
Backports is for programs that get released after a main ubuntu release,

say a new version of Xine or something,  if someone requests it, and it isnt too much hastle, a backports dev will make it for download.

Its a really useful thing.

(that may not be the actual process of what goes on, but its something like that)

[https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)



PS thanks for the correct line for sources.list!

---

### Post by BoyOfDestiny on 2006-06-08
[QUOTE=darkdigger]Thanks christhemonkey. I indeed didn't have multiverse enabled. So what's the difference between the backports and regular repository? and why isn't the regular multiverse repository placed in the sources.list by default (even if it's just disabled)?
-Arash[/QUOTE]

I thought it was. Did you upgrade form an old dapper or modify the sources list yourself (since the #cdrom stuff is gone...) 

I've told people to enable it graphically, from software properties, universe should be with multiverse... Am I wrong (I've had the same sources.list for like 1/2 year, so I'm not 100% sure...)?

---

### Post by harishg on 2006-06-08
easyubuntu did the work of getting from those repositories.

---

### Post by darkdigger on 2006-06-08
BoyOfDestiny,
I did a fresh install, so no it wasn't there. The default repos are listed in my post above (minus the beerorkid repo).

-Arash

---


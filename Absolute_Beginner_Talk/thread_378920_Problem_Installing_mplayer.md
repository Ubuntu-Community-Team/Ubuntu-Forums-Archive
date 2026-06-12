---
title: "Problem Installing mplayer"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-03-07
I want to play mp3's in the Firefox browser and I understand mplayer plugin may enable me to do that. However, I get an error message when I try to install it in terminal: 

me@mymachine:/usr/lib/firefox/plugins$ sudo apt-get install mplayer mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate

When I use Synaptic, I get this message: 

mozilla-mplayer:
 Depends: mplayer (>=1.0-pre5) but it is not installable or
 	mplayer-nogui (>=1.0-pre5) but it is not installable or
 	mplayer-powerpc (>=1.0-pre5) but it is not installable or
 	mplayer-g4 (>=1.0-pre5) but it is not installable

I'm using Dapper Drake 6.06 and Firefox 2.0.0.1

---

### Post by taurus on 2007-03-07
Have you enabled both universe and multiverse in /etc/apt/sources.list first?

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Sleestack on 2007-03-07
Yes, they've been enabled.

---


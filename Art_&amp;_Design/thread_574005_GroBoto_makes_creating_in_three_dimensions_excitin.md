---
title: "GroBoto makes creating in three dimensions exciting and enjoyable!"
date: 2007-10-12
forum: Art &amp; Design
---

### Post by MozartlovesUbun2 on 2007-10-12
[http://www.groboto.com/GroMobile.html](http://www.groboto.com/GroMobile.html)

[http://www.groboto.com/index.html](http://www.groboto.com/index.html)

Havn't tried it out yet myself, does anyone know of **linux version** for this?

what i'm most interested is the** kinetic 3D Gizmos on your desktop.**

*These simple games, puzzles and kinetic sculptures are unlike anything you&#8217;ve ever seen on your desktop (or anywhere else).*

check out some videos at youtube, etc...

---

### Post by fktt on 2007-10-12
seems theres no native for linux. :/ havent tried trough wine either.. :(

---

### Post by Steveway on 2007-10-12
So it's just some 3D-thingies on your Desktop?
Macslow has made the same thing.
[http://gitweb.freedesktop.org/?p=users/macslow/rgba-glx;a=summary](http://gitweb.freedesktop.org/?p=users/macslow/rgba-glx;a=summary)
You need a compositing-manager to remove the black rectangle around it.
To get it running do this:
Open a terminal and type the following:
> git clone git://people.freedesktop.org/~macslow/rgba-glx rgba
> cd rgba
> sh autogen.sh
> ./configure
> make
Done, and to run it type this from that same terminal:
> cd src
> ./rgba-glx
Then you should see a rotating sphere.
Check the included README for more information.
If there is really demand for such things like this grobot then take Mircos code and use it to make your own 3D-thingies.

---

### Post by tlepes on 2008-05-01
I tried Steveway's commands, but the 'git' command is not available on my system.  I tried **sudo aptitude install git** (and it did), but I still have no git command.

Ideas? IANASD (I am not a software developer)

Tim

---

### Post by zekopeko on 2008-05-01
try git-core instead git

---

### Post by tlepes on 2008-05-01
> **zekopeko said:**
> try git-core instead git

thanks for the suggestion but still no joy :(

```
output for tab-completion at propmt...
mojo@alembic:~/src$ git
gitaction    gitfm        gitmkdirs    gitps        gitrfgrep    gitunpack    gitwhich     gitxgrep     
gitdpkgname  gitkeys      gitmount     gitregrep    gitrgrep     gitview      gitwipe      
mojo@alembic:~/
```

am i missing a package to install with git?
(ubuntustudio 8.04 amd64)

Tim

---


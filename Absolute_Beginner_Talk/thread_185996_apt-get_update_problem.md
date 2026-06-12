---
title: "apt-get update problem"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-06-01
I am getting this error when ever i try to run

sudo apt-get update

it worked fine before, now I am getting errors. Does anyone know what my problem could be. Thank you for any help.

Here is my error:

> 
grim918@ubuntu:/$ sudo apt-get update
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release.gpg
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Err [http://theli.free.fr](http://theli.free.fr) ./ Packages
  404 Not Found
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
  404 Not Found
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
  404 Not Found
Get:5 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Fetched 5B in 1m33s (0B/s)
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
grim918@ubuntu:/$


---

### Post by ash211 on 2006-06-01
Some of the repositories you have in your /etc/apt/sources.list aren't functioning any more.  Try running ```
sudo nano /etc/apt/sources.list
``` and commenting out (put a '#' at the beginning of the line) the ones that apt-get can't find.  

From first glance, it looks like the koti.mbnet.fi and theli.free.fr repositories are the ones not working.  Comment those out and reply back if that fixed things.

---

### Post by grim918 on 2006-06-01
ok that fixed the problem. thank you very much.

---

### Post by ash211 on 2006-06-01
[QUOTE=grim918]ok that fixed the problem. thank you very much.[/QUOTE]
You're welcome!

---


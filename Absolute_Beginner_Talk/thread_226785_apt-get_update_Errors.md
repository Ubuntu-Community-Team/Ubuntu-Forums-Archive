---
title: "apt-get update Errors?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by BitTorrentBuddha on 2006-07-31
I'm trying to isntall init.ng using [this tutorial](https://help.ubuntu.com/community/InitNG). I've made it to the point where I have to apt-get update. However the snag in the road is that each time I fail to connect with any repositories. I need the debian space-based.de repositories for the next step and I'm lost at (that which I assumed to be) the easiest step.```
Ign http://compiztools.free.fr unstable Release.gpg
Ign http://compiztools.free.fr unstable Release
Ign http://compiztools.free.fr unstable/main Packages
Hit http://compiztools.free.fr unstable/main Packages
Err http://xgl.compiz.info dapper Release.gpg
  Temporary failure resolving 'xgl.compiz.info'
Err http://idefix.eup.uva.es ./ Release.gpg
  Temporary failure resolving 'idefix.eup.uva.es'
Err http://debian.space-based.de experimental Release.gpg
  Temporary failure resolving 'debian.space-based.de'
Err http://www.getautomatix.com dapper Release.gpg
  Temporary failure resolving 'www.getautomatix.com'
Err http://security.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Ign http://people.ubuntu.com ./ Release.gpg
Ign http://people.ubuntu.com ./ Release
Ign http://people.ubuntu.com ./ Packages
Hit http://people.ubuntu.com ./ Packages
Get:1 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Ign http://theli.free.fr ./ Release.gpg
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Ign http://theli.free.fr ./ Release
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://theli.free.fr ./ Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Err http://theli.free.fr ./ Packages
  404 Not Found
Fetched 2B in 34s (0B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://www.getautomatix.com/apt/dists/dapper/Release.gpg  Temporary failure resolving 'www.getautomatix.com'
Failed to fetch http://xgl.compiz.info/dists/dapper/Release.gpg  Temporary failure resolving 'xgl.compiz.info'
Failed to fetch http://idefix.eup.uva.es/paquetes/gaim2.0/./Release.gpg  Temporary failure resolving 'idefix.eup.uva.es'
Failed to fetch http://debian.space-based.de/debs/dists/experimental/Release.gpg  Temporary failure resolving 'debian.space-based.de'
Failed to fetch http://theli.free.fr/packages/dapper/./Packages.gz  404 Not Found
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by ciscosurfer on 2006-07-31
The [initng page]("https://help.ubuntu.com/community/InitNG") says the dapper package is broken but that you can still build from the source package.

---

### Post by Lord Illidan on 2006-07-31
Can you give us your sources.list?

---

### Post by BitTorrentBuddha on 2006-07-31
That's included in the instructions, the space-based.de repository is where you get the source package I believe. Also, waiting 20 minutes and re-running the command let me access the repository. But now the gpg isn't working. ```
$ gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 77AFC5B7
gpg: requesting key 77AFC5B7 from hkp server wwwkeys.eu.pgp.net
gpg: key 77AFC5B7: "Armin Berres <a.berres@web.de>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
$ gpg --armor --export 77AFC5B7 | apt-key add -
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error
```

---

### Post by ciscosurfer on 2006-07-31
Here's a quick workaround (forget the repo for the time being):  Use wget to grab the page and download/install with dpkg after you've done that (resolve dependency issues before doing this; get necessary programs to build from source as well [build-essential, and others])```
wget http://debian.space-based.de/debs/pool/main/i/initng/
wget http://debian.space-based.de/debs/pool/main/i/initng-ifiles/
```Then follow the rest of the instructions.  Should work just fine.

---

### Post by BitTorrentBuddha on 2006-08-01
I think I'm going to let initng be until I'm a little more experienced, I don't reboot all that often anyway. I am getting these errors all the time while updating my sources.list. I can access the internet just fine for anything else, inculding installing with apt-get when updating does work. But here is my sources.list:```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://www.getautomatix.com/apt dapper main

deb http://theli.free.fr/packages/dapper/ ./
deb http://people.ubuntu.com/~seb128/deb ./
deb http://compiztools.free.fr/debian unstable main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
deb http://idefix.eup.uva.es/paquetes/gaim2.0/ ./
deb http://debian.space-based.de/debs/ experimental main
deb-src http://debian.space-based.de/debs/ experimental main
```

---


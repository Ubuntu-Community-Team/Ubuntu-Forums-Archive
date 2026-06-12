---
title: "problems with upgrading to edgy from dapper."
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-10-26
I'm trying to upgrade dapper to edgy all day long.
but I have many problems in every way I go.

when I do : gksu update-manager -c
I get :
Cannot install all available updates
Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.
the following updates will be skipped :
build-essential
dpkg-dev
fakeroot
g++
libc6-dev

when I go to synoptic and try to update from there , I'm in the middle of dependencies HELL
every package I need to update asks me to search and remove lots other packages.

and when I click upgrade in the update manager then I get :

Error during update
A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://users.lichtsnel.nl/~seveas/dists/dapper-seveas/Release.gpg](http://users.lichtsnel.nl/~seveas/dists/dapper-seveas/Release.gpg) Could not connect to users.lichtsnel.nl:80 (83.137.151.2). - connect (113 No route to host)
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg) Could not connect to cipherfunk.org:21 (205.178.189.131), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [http://users.lichtsnel.nl/~seveas/dists/dapper-seveas/all/source/Sources.gz](http://users.lichtsnel.nl/~seveas/dists/dapper-seveas/all/source/Sources.gz) Could not connect to users.lichtsnel.nl:80 (83.137.151.2). - connect (113 No route to host)
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz) Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz) Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

when I try to upgrade from the alternative cd with this command :
 gksu sh /cdrom/cdromupgrade 
I get :
Could not calculate the upgrade
An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

and if I do : maxim@maxim-home:~$   sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

what can I do ? 
I do not want to make a clean install , b/z I have important data and programs I fought to install.
how can I upgrade ?

---

### Post by evolvedlight on 2006-10-26
Have you tried running ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
```?

Steve

---

### Post by MaximB on 2006-10-26
yes I have , there are so many ways to do this that I forgot to write it all ;)

```
maxim@maxim-home:~$ sudo apt-get update
Password:
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Errftp://cipherfunk.org dapper Release.gpg
  Read error - read (104 Connection reset by peer)
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get: 3 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 4 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 5 [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release.gpg [307B]
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Get: 6 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Get: 7 [http://deb.opera.com](http://deb.opera.com) etch Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release
Errhttp://seveas.theplayboymansion.net dapper-seveas Release

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch Release
Errhttp://deb.opera.com etch Release

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Get: 8 [http://deb.opera.com](http://deb.opera.com) etch Release [867B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Get: 9 [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release [34.2kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [38.0kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [38.0kB]
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Get: 12 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
85% [10 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [9 Releasbzip2: (stdin) is not a bzip2 file.
Errhttp://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
85% [11 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [9 Releasbzip2: (stdin) is not a bzip2 file.
Errhttp://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [38.0kB]
87% [Waiting for headers] [Waiting for headers] [9 Release gpgv 2435/34.2kB 7%]bzip2: (stdin) is not a bzip2 file.
Errhttp://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [38.0kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
90% [Waiting for headers] [9 Release gpgv 6479/34.2kB 18%] [Connecting to usersbzip2: (stdin) is not a bzip2 file.
Errhttp://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Get: 15 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
Get: 16 [ftp://ftp.gwdg.de](ftp://ftp.gwdg.de)  Release.gpg
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper Release
Ign [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper/main Sources
Hit [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas/all Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper/universe Sources
Errhttp://users.lichtsnel.nl dapper-seveas Release.gpg
  Could not connect to users.lichtsnel.nl:80 (83.137.151.2). - connect (113 No route to host)
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) dapper/multiverse Sources
Get: 17 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Get: 18 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Ign [ftp://ftp.gwdg.de](ftp://ftp.gwdg.de)  Release.gpg
Get: 19 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Get: 20 [ftp://ftp.gwdg.de](ftp://ftp.gwdg.de)  Release
Ign [http://users.lichtsnel.nl](http://users.lichtsnel.nl) dapper-seveas Release
Ign [ftp://ftp.gwdg.de](ftp://ftp.gwdg.de)  Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Hit [ftp://ftp.gwdg.de](ftp://ftp.gwdg.de)  Packages
Get: 21 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Get: 22 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Get: 23 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Ign [http://users.lichtsnel.nl](http://users.lichtsnel.nl) dapper-seveas/all Sources
Errftp://ftp.free.fr dapper/free Packages
  Unable to fetch file, server said ‘Failed to open file.  ’
Get: 24 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Errftp://ftp.free.fr dapper/non-free Packages
  Unable to fetch file, server said ‘Failed to open file.  ’
Get: 25 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Errftp://ftp.free.fr dapper/free Sources
  Unable to fetch file, server said ‘Failed to open file.  ’
Errhttp://users.lichtsnel.nl dapper-seveas/all Sources
  Could not connect to users.lichtsnel.nl:80 (83.137.151.2). - connect (113 No route to host)
Get: 26 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Errftp://ftp.free.fr dapper/non-free Sources
  Unable to fetch file, server said ‘Failed to open file.  ’
Errhttp://au.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (130.95.128.79), connection timed out
Errftp://cipherfunk.org dapper Release

Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper/main Packages
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper/main Sources
Errftp://cipherfunk.org dapper/main Packages
  Could not connect to cipherfunk.org:21 (205.178.189.131), connection timed outErrftp://cipherfunk.org dapper/main Sources
  Could not connect to cipherfunk.org:21 (205.178.189.131), connection timed outFetched 35.6kB in 10m0s (59B/s)
Failed to fetch [http://users.lichtsnel.nl/~seveas/dists/dapper-seveas/Release.gpg]("http://users.lichtsnel.nl/%7Eseveas/dists/dapper-seveas/Release.gpg")  Could not connect to users.lichtsnel.nl:80 (83.137.151.2). - connect (113 No route to host)
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg)  Read error - read (104 Connection reset by peer)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (130.95.128.79), connection timed out
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [http://users.lichtsnel.nl/~seveas/dists/dapper-seveas/all/source/Sources.gz]("http://users.lichtsnel.nl/%7Eseveas/dists/dapper-seveas/all/source/Sources.gz")  Could not connect to users.lichtsnel.nl:80 (83.137.151.2). - connect (113 No route to host)
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-i386/Packages.gz](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Could not connect to cipherfunk.org:21 (205.178.189.131), connection timed out
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/source/Sources.gz](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/source/Sources.gz)  Could not connect to cipherfunk.org:21 (205.178.189.131), connection timed out
Reading package lists... Done
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.
```


```
maxim@maxim-home:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  build-essential dpkg-dev fakeroot g++ libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

---

### Post by wirelessmonkey on 2006-10-26
You need to edit /etc/apt/sources.list and replace all instances of "dapper" with "edgy"

save sources.list

sudo apt-get update
sudo apt-get dist-upgrade


It's gonna take awhile, Edgy is being downloaded by a bajillion people at the moment.

---

### Post by MaximB on 2006-10-26
to save space I'm only going to write the second command :

maxim@maxim-home:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
[B]The following packages have been kept back:
  build-essential dpkg-dev fakeroot g++ libc6-dev[/B]
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

the problem is different 
it's a dependencies problem that I don't know how to solve the easy way.

---

### Post by rowanparker on 2006-10-26
I recall *sudo apt-get install -f* but that might be do to with something else.

---

### Post by dhalgren on 2006-10-26
> **MAXDDARK said:**
> I'm trying to upgrade dapper to edgy all day long.
but I have many problems in every way I go.

when I do : gksu update-manager -c


Max, in the post in edgy development that i used to do the upgrade, it said to use the following:

sudo gksu update-manager -c -d

The reason given there was that the -d switch needs to be explicitly called in dapper.

that is what i did and it worked as i mentioned elsewhere (to you).

sudo apt-get -f install apparently fixes any dependency probs after having done a sudo apt-get upgrade.  (although i would run an apt-get update before the upgrade option.

anyway, give the update-manager anotehr go with the -d and -c opption and see what happens. It certainly did it for me.

---

### Post by MaximB on 2006-10-27
the  gksu "update-manager -c -d" got the same results as without a "-d"....
it's a dependencies problem.

---

### Post by dhalgren on 2006-10-27
> **MAXDDARK said:**
> the  gksu "update-manager -c -d" got the same results as without a "-d"....
it's a dependencies problem.

hmm... have you updated your repos?
and then done an upgrade?

do you have any non-ubuntu (non-official) repos enabled?

I had to disable some non-official (as in non-ubuntu) repos....so if you are using any, disable them in your preferred manner (comment out in the file or uncheck in synaptic settings) and then try updating and upgrading.

i don't know whether this will work, I am just trying to think of anything that might help other than a fresh dapper install.

---

### Post by MaximB on 2006-10-27
the non-official repros are disabled during the installation automatically.
and I cannot update b/z of the dependencies hell.
my version of * needed for other programs to work , so I cannot update 
and it's very hard to go to every single program and solve her dependencies one by one.

---

### Post by dhalgren on 2006-10-27
> **MAXDDARK said:**
> the non-official repros are disabled during the installation automatically.
They weren't when I did it, I had to do it manually.
> and I cannot update b/z of the dependencies hell.
my version of * needed for other programs to work , so I cannot update 
and it's very hard to go to every single program and solve her dependencies one by one.

I don't know what to suggest, then, unless it is to uninstall the programs that have the dependency problem, but you may not know what they are? 
if 

apt-get update
apt-get -f install   and
apt-get upgrade

don't solve the problem, then i am at a loss. Sorry about that.

the only other thing i can suggest is that you try aptitude.  I have read that it handles dependencies more effectively than apt-get. (i think i read that in mod-free, or maybe jozef posted it?)

---

### Post by MaximB on 2006-10-27
the aptitude indeed works IF you installed the program with aptitude.
if you did it with apt-get , aptitude won't help.

---

### Post by dhalgren on 2006-10-27
> **MAXDDARK said:**
> the aptitude indeed works IF you installed the program with aptitude.
if you did it with apt-get , aptitude won't help.

ah, ok. I have never really used it, so i didn't know.

---

### Post by xpod on 2006-10-27
> ah, ok. I have never really used it, so i didn't know.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

A lot better apparently

---

### Post by Malakia on 2006-10-27
I use aptitude all the time and I like it. Also I upgraded fro dapper to edgy and it hosed up my bootup and I tried both ways of fixing it and it still wouldn't work so I reinstalled and I think I'm going to stay with dapper for a while.

---


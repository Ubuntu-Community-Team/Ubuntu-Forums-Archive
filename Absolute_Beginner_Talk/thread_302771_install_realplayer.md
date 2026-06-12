---
title: "install realplayer"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-11-19
Hello,

To install realplayer on ubuntu 6.06 I get the message of xlibs is not installable. What is wrong?
Could you guide me please?

---

### Post by madmetal on 2006-11-19
try install it from synaptic or automatix.

---

### Post by linux-beginner on 2006-11-19
I've done it, but no result.

---

### Post by linux-beginner on 2006-11-19
This is a screenshot of the error.

---

### Post by Perfect Storm on 2006-11-19
How's your sourcelist looks like?

```
cat /etc/apt/sources.list
```

---

### Post by linux-beginner on 2006-11-19
It is:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiversedeb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted


---

### Post by LLRNR on 2006-11-19
@ linux-beginner : It's always better to keep your questions within the same thread... I gave you an answer in the OTHER "xlibs" thread... Check it out, download RealPlayer from their site and give it a try ok ?

---

### Post by Perfect Storm on 2006-11-19
I have closed the other thread. It's bad ethic to run multiply threads about the same issue.


You sourcelist is mess. What have you done with it?

Check here to make a new list: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by linux-beginner on 2006-11-19
ok.
Thanks

---

### Post by linux-beginner on 2006-11-19
I have up graded my ubuntu 5.10 Serever to ubuntu 6.06 desktop.

---

### Post by Perfect Storm on 2006-11-19
Well take a look at the link I gave you and build up a new list. No wonder you have trouble :)

Just leave out the Kubuntu/KDE stuff if you don't use KDE/kubuntu.

---

### Post by linux-beginner on 2006-11-19
I've done it. The sources.list liks:
> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bleeding edge wine packages (sources)
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./


---

### Post by Perfect Storm on 2006-11-19
then 
sudo aptitude update && sudo aptitude upgrade

Afterwards try install realplay

---

### Post by linux-beginner on 2006-11-19
I get the same error again.

---

### Post by Perfect Storm on 2006-11-19
okay.

Try with:
```
sudo aptitude install realplay
```

See if it solves the problem or post the outcome. (remember to close synaptic and other installer applications)

---

### Post by linux-beginner on 2006-11-19
This is the result:

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  realplayer
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.5kB of archives. After unpacking 213kB will be used.
The following packages have unmet dependencies:
  realplayer: Depends: xlibs which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.


---

### Post by Perfect Storm on 2006-11-19
By the way did you add the new sources into the sourcelist?

---

### Post by linux-beginner on 2006-11-19
I haven't added but replaced.
My sources.list likes now:
> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by Perfect Storm on 2006-11-19
You nee the whole list if you want the non-GPL stuff also.

```
sudo nano /etc/apt/sources.list
```
replace everything with the list from the source generator.
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by linux-beginner on 2006-11-19
the flowing is what I have done.
> guus@ubuntu:~$ sudo nano /etc/apt/sources.list
guus@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates Release
Get:3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/main Packages [619kB]
Get:4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/restricted Packages [4571B]
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/restricted Sources
Get:5 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:6 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/multiverse Sources
Fetched 3177kB in 18s (167kB/s)
Reading package lists... Done
guus@ubuntu:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
guus@ubuntu:~$


I get again the same error!:(

---

### Post by Perfect Storm on 2006-11-19
Okay, lets try something diffrent then.

add this to your sourcelist:

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


then:
```
sudo aptitude update
sudo aptitude install realplay
```

---

### Post by linux-beginner on 2006-11-19
It made possible I could install realpayer 10. I had the version 8 on Synaptic Package Manager. Now it's installed (Version 10).
Could you say me what was happenning? What were the leaste 3 rules that I added to Sources.list
Thanks for all,

---

### Post by Perfect Storm on 2006-11-19
It's for commercial/non-GPL application an alike. I just remembered that PLF have removed their version of Realplayer 10.

But if you want GPL player that can handle realplayer stuff, I suggest mplayer to be the best bet.

---


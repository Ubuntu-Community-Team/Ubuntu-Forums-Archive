---
title: "why cant i install stuff?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-10-04
sources list
```
gail@buttmunch:~$ sudo cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
gail@buttmunch:~$
```

i dunno if it's internet or dependencies or wot but i cant even do update && upgrade w/o issue. maybe if this gets fixed i can install java & mp3 like normal?

```
gail@buttmunch:~$ sudo aptitude update && sudo aptitude upgrade
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release             
Ign http://us.archive.ubuntu.com feisty/main Packages               
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Get:4 http://us.archive.ubuntu.com feisty/main Packages [1307kB]
Get:5 http://us.archive.ubuntu.com feisty/main Sources [385kB]
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Get:6 http://us.archive.ubuntu.com feisty/universe Sources [1523kB]
99% [4 Packages gzip 0]           
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/main Packages
  Sub-process gzip returned an error code (1)
99% [5 Sources gzip 0] 
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/main Sources
  Sub-process gzip returned an error code (1)
99% [6 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/universe Sources
  Sub-process gzip returned an error code (1)
Fetched 6B in 1s (3B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
gail@buttmunch:~$
```

---

### Post by Perfect Storm on 2007-10-04
Have you tried rebuilding your sourcelist?

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Also try another mirror than "us"

---

### Post by Acglaphotis on 2007-10-04
Try this:

1) Comment everything in you sources.list.

2) do a

```

sudo aptitude update

```

3) De-comment your sources.

4) Do step 2 again.

Let us know how it went.

---

### Post by lunaz on 2007-10-04
woohoo ty!!

using the sources list generator helped, the only diff was adding the ca. instead of the us. for country

---

### Post by Zootropo on 2007-10-04
You can change the mirror you use from System -> Administration -> Source origins

---

### Post by Sef on 2007-10-04
> You can change the mirror you use from System -> Administration -> Source origins

I think you mean from System -> Administration -> Software Sources

---


---
title: "apt-get update universe sources trouble"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Dymn on 2007-04-24
Hi, I'm new to the game, just installed Feisty.
First time getting Linux to work for me since I first tried about 8 years ago, so I'm very pleased.
One problem, which I have searched for but not found.
Running apt-get update, everything works fine until:

```

Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources [1523kB]            
99% [9 Sources gzip 0]                                                102B/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
  Sub-process gzip returned an error code (1)
Fetched 33.9kB in 23s (1444B/s)                                                
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I've gone to the site and downloaded it manually, but I don't know how to install the package.
Can someone help me out?

Thanks

---

### Post by xyz on 2007-04-24
Hi,
Check this out:
[How to install anything]("http://monkeyblog.org/ubuntu/installing/")
Hope it helps.

---

### Post by Dymn on 2007-04-24
After trying to extract the manually downloaded Sources.gz:

```

gzip: /tmp/fr-nl36KS/Sources.gz: unexpected end of file

```

:-k

---

### Post by Sef on 2007-04-24
Could you post your sources list?

First open the Terminal.  (Applications > Accessories > Terminal)

Then type this code:

```
gksudo gedit /etc/apt/sources.list
```

The copy and paste your sources list here.

---

### Post by Dymn on 2007-04-24
here is my sources list:

```

# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
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

```

---

### Post by Dymn on 2007-04-25
bump, can someone help me out with this?

Thanks

---

### Post by tekguy on 2007-04-25
I am having the same exact issue too.

---

### Post by kadath on 2007-04-25
I'm also having this same issue.

---

### Post by kadath on 2007-04-25
Here's the exact error I get:

```
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.bz2: Sub-process bzip2 returned an error code (2)
```

If I download those packages manually, what do I do with them?

---

### Post by Dymn on 2007-04-25
OK, I fixed it.
For you who have the same trouble:
Open Synaptic:
At top of screen:
System > Administration > Synaptic Package Manager
enter root password
At top:
Settings > Repositories
In the Ubuntu Software tab,
Make sure all boxes under 'Downloadable from the Internet' are checked then change
Download from: Server for United States to
Main Server

Click close, click close again on the dialog that pops up, then hit reload. It should download all of the packages in question.

---

### Post by kadath on 2007-04-25
> **Dymn said:**
> OK, I fixed it.
For you who have the same trouble:
Open Synaptic:
At top of screen:
System > Administration > Synaptic Package Manager
enter root password
At top:
Settings > Repositories
In the Ubuntu Software tab,
Make sure all boxes under 'Downloadable from the Internet' are checked then change
Download from: Server for United States to
Main Server

Click close, click close again on the dialog that pops up, then hit reload. It should download all of the packages in question.

Gah, why didn't I think of that? Thanks for reminding me of this, Dymn.

---


---
title: "Where is libapache2-mod-auth-mysql"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by Gregory Hansen on 2006-04-03
I have been through AddingRepositoriesHowTo and I have started going through the ApacheMySQLPHP wiki. Installing Apache 2 and Installing PHP 4 seemed to work OK. In "Installing MySQL 4" in the ApacheMySQLPHP wiki at [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) my system says it "Couldn't find libapache2-mod-auth-mysql" and I can't find it in my synaptic package manager. I see several other libapache2-mod-auth items, but not mysql.

Where should I look for libapache2-mod-auth-mysql?

Thanks a bunch,
Gregory.

 Running Breezy Badger 5.10

---

### Post by linear on 2006-04-03
Odd. I can see it plain as day in Synaptic.

This doesn't work?
 [FONT=Verdana]```
$ sudo apt-get install libapache2-mod-auth-mysql
``` 
Are you sure you have the correct repositories enabled?
[/FONT]

---

### Post by Gregory Hansen on 2006-04-03
Absolutely not.  I think that's what I'm asking. Which repository should I have enabled?

I currently have
- CD Ubuntu 5.10 "Breezy Badger" (Binary)
- Ubuntu 5.10 "Breezy Badger" (Binary) Community maintained (Universe) and Non-free (Multiverse)
- Ubuntu 5.10 "Breezy Badger" (Source) Community maintained (Universe) and Non-free (Multiverse)
- [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports (Binary) main restricted universe multiverse
- [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports (Source) main restricted universe multiverse

---

### Post by catlett on 2006-04-03
I have the program you want in my synaptic manager.  If you want, you can  copy my list to your source list. My list comes from the Automatix program. You can do two things. You can leave my list as your source list or make a backup of your list and erase my list after you get the program. 
To get your list type ```
sudo gedit /etc/apt/sources.list 
```
This will get your list opened. Copy and paste my list to yours. Save the list. Go to the terminal and type ```
sudo apt-get update
```
Then open synaptic manager and scroll down to the program. Then replace your old list or leave mine in, it's up to you
> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

## created by arniesourcewrite

---

### Post by Gregory Hansen on 2006-04-04
That was a really big help. I can now see mysql-server and libapache2-mod-auth-mysql in my repository.

I really appreciate the help, and I hate to be a bother, however, now when I run the commands, while most of it runs OK, I am getting a few messages indicating an error with some of the ftp stuff.

```
Get:38 ftp://ftp.free.fr breezy/free Packages
Err ftp://ftp.free.fr breezy/free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:39 ftp://ftp.free.fr breezy/non-free Packages
Err ftp://ftp.free.fr breezy/non-free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:40 ftp://ftp.free.fr breezy/free Sources
Err ftp://ftp.free.fr breezy/free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:41 ftp://ftp.free.fr breezy/non-free Sources
Err ftp://ftp.free.fr breezy/non-free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Fetched 335kB in 1m55s (2890B/s)
Failed to fetch ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breez y/free/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to ope n file.  '
Failed to fetch ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breez y/non-free/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to  open file.  '
Failed to fetch ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breez y/free/source/Sources.gz  Unable to fetch file, server said 'Failed to open file .  '
Failed to fetch ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breez y/non-free/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '
Reading package lists... Done
W: GPG error: http://kubuntu.org breezy Release: The following signatures couldn 't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D50 88
W: GPG error: http://koti.mbnet.fi breezy/ Release: The following signatures cou ldn't be verified because the public key is not available: NO_PUBKEY E8DDB291701 88C3B
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_ma in_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/restr icted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backpo rts_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/unive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backport s_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/multi verse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backpo rts_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

```

By the way, the above errors were AFTER I ran apt-get update as it suggested..

Thanks again,

Gregory

---

### Post by linear on 2006-04-05
Unless you have a reason to use the ftp.free.fr repository, just comment out or delete the lines in sources.list that contain it.
 
Catlett's sources.list looks to have some duplicate lines. You can get rid of those as well.

---


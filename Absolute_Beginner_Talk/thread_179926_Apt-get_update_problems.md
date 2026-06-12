---
title: "Apt-get update problems"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by tijean on 2006-05-21
Hello, 

I just installed ubuntu and it just can't upgrade. 
I changed /etc/apt/sources.list and added the mutiverse repositories

When when I  "sudo apt-get update"  I always get the following errors. 

These in the beginning after[COLOR="Gray"] "Ign cdrom.... "[/COLOR]
I get: 
	[COLOR="Gray"]"Err cdrom: ...."
     	"   Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs[/COLOR]



En then downloading of packages starts en afterwards a get a number of differents errors: 

[COLOR="Gray"]"Err [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) breezy/restricted Packages
  Sub-process gzip returned an error code (1)"[/COLOR]

[COLOR="Gray"]
"Get:27 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) breezy/restricted Sources [1363B]
Err [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) breezy/restricted Sources
  Error reading from server - read (104 Connection reset by peer)"

"Failed to fetch ....."

"W: Couldn't stat source package list [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/be.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)"


"W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead."[/COLOR]


Can somoene explain me why a clean update is not possible ? 
If haven't given enough information about my problem let me know
 Thanks

---

### Post by Kethinov on 2006-05-21
Post the contents of your **/etc/apt/sources.list**, though my first guess would be you need to get rid of any lines citing cdroms as apt sources and place internet sources in their place.

---

### Post by tijean on 2006-05-21
[COLOR="Gray"]#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) breezy multiverse
[/COLOR]

I just commented the first line and ran apt-get update again and i still get the errors:
[COLOR="Gray"]
- Sub-process gzip returned an error code (1)"
-Error reading from server - read (104 Connection reset by peer)
-Failed to fetch 
-W: Couldn't stat source package
-W: You may want to run apt-get update to correct these problems
-E: Some index files failed to download, they have been ignored, or old ones used instead.
[/COLOR]

---

### Post by Kethinov on 2006-05-21
Try changing those mirrors from be.archive.ubuntu.com to just archive.ubuntu.com and see if that fixes things.

---

### Post by zxcv70 on 2006-05-21
You have problem in 'updating' or 'upgrading' ? If updating, so you should delete unnecessary addresses which caused problems in source.list. 
And if you want to upgrade just type 'sudo apt-get dist-upgrade'.

---

### Post by tijean on 2006-05-21
First i change as Kethinov said from be.archive... to archive ... 

I get kind of the same erros en some new ones too: 

[COLOR="Gray"]-416 Requested Range Not Satisfiable [IP: ...]
-W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG  .....[/COLOR]

I don't know if it's all related or maybe different problems.


Then I only selected a few adresses from where to update. 
So my sourcesfiles looks like this: 
------------------
[COLOR="Gray"]#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

###deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
###deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

###deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
###deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

###deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
###deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

###deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse
[/COLOR]

--------------------------------------
And i get the following:

[COLOR="Gray"]Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [585kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [5061B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [305kB]
99% [5 Sources gzip 0] [3 Packages bzip2 1687552]                                                                                                60.5kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Sub-process gzip returned an error code (1)
Fetched 621kB in 11s (55.5kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tijean@MusicPc:/etc/apt$[/COLOR]


But sometimes i get more errors. Is this normal ? 
Thanks for helping.

---

### Post by zxcv70 on 2006-05-21
Well, if it makes errors so it shouldn't be OK.
Try this thread. Theres a sample source.list you can use:

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---


---
title: "Apt - Multiverse repositories not working"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by popcorn09 on 2006-09-16
Hi,

When I do **apt-get update** I get the following error towards the end:

[I]gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Fetched 95B in 5s (19B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/) Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.[/I]

My sources.list file is below. Can anyone help me fix this please?
> deb file:/var/cache/apt-build/repository apt-build main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
## Repository for Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
# Google Picasa for Linux repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Thanks.

---

### Post by oedipuss on 2006-09-16
I think its just the sources list that isn't being downloaded. I could be wrong though ... Try to remove 'multiverse' from the 10nth line of your sources.list (the one starting with 'deb-src') and see if the error persists. 
If it's indeed just about source code packages, you can ignore it.

---

### Post by hoagie on 2006-09-16
Try removing that source that oedippus said. If it does not work I could give you my sources.list that works fine:D

---

### Post by popcorn09 on 2006-09-16
> **oedipuss said:**
> I think its just the sources list that isn't being downloaded. I could be wrong though ... Try to remove 'multiverse' from the 10nth line of your sources.list (the one starting with 'deb-src') and see if the error persists. 
If it's indeed just about source code packages, you can ignore it.

That works. Why did it happen though? And why do I not need the source code packages? Are they not required for anything?

Thanks! :)

---


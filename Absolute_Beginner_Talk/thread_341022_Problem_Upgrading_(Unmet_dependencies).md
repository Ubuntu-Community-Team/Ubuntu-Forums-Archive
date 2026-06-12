---
title: "Problem Upgrading (Unmet dependencies)"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Xummoner on 2007-01-18
Hey guys, this is my first post, and I hope I'm not repeating something (I used search but couldn't find anything).
Here's my problem:
I started using Ubuntu like a month ago, was loving it so far but then some problems came (or maybe I'm just a bit stupid), there's a lot of problems I've been having lately trying to get a bit more out of ubuntu (with no success yet) but here's the one that annoys me the most, when I try to "sudo aptitude upgrade" I get this error:

```
david@David-Desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages have unmet dependencies:
  libecore1-desktop: Depends: libecore1 (>= 0.9.9.037) which is a virtual package.
                     Depends: libecore1-file which is a virtual package.
```

I tried using Synaptic to upgrade and update, but it won't work.

Do I have to install Ubuntu all over again, or is there any way to fix that, and another thing, upgrading to edgy eft would do any good? or I would lose configurations and stuff? (I don't want to configure my video card again, cuz it was a real PITA)...

Hope someone can help me.

Edit**

This is exactly what the package manager displays:
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by bapoumba on 2007-01-18
Hello,
what release of ubuntu are you using ? I cannot find libecore1-desktop on dapper or edgy. Do you have additional repositories in your sources.list ?
Please post the output to **cat /etc/apt/sources.list**.

---

### Post by Xummoner on 2007-01-18
Yes, I've installed some additional repos, I'm on Ubuntu Dapper.

Here's my SourceList:

```
david@David-Desktop:~$ cat /etc/apt/sources.list

deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

deb http://ubuntu.beryl-project.org dapper main

deb-src http://ubuntu.beryl-project.org dapper main

deb http://ubuntu.beryl-project.org/ dapper main aiglx

deb http://gefechtsdienst.de/uman/files/ unstable main

deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
#GMail Notifier
```

---

### Post by bapoumba on 2007-01-18
Looks to me that libecore* packages giving you trouble come from the debian repo in your sources.list :
[http://gefechtsdienst.de/uman/files/]("http://gefechtsdienst.de/uman/files/").
Comment that repo out and run the update again.

(not such a good idea to mix up repositories from other distributions in the sources.list file, and upgrading from them. Very often you can break the system if some libraries are upgraded to versions incompatible with Ubuntu's)

---

### Post by Xummoner on 2007-01-18
Thanks for your reply, I already took that entry from my sources list but now I'm getting another couple of errors, here's what apt-get update says:

```
david@David-Desktop:~$ sudo apt-get update
Get: 1 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get: 2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get: 3 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get: 4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get: 5 http://ubuntu.beryl-project.org dapper Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Get: 6 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get: 7 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Get: 8 http://security.ubuntu.com dapper-security Release [50.9kB]
Get: 9 http://ubuntu.beryl-project.org dapper Release [2965B]
Get: 10 http://archive.ubuntu.com dapper-backports Release [38.4kB]
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://ubuntu.beryl-project.org dapper/main Packages
Hit http://ubuntu.beryl-project.org dapper/main Sources
Hit http://ubuntu.beryl-project.org dapper/main Packages
Hit http://archive.ubuntu.com dapper-updates Release
Get: 11 http://archive.ubuntu.com dapper-security Release [50.9kB]
Get: 12 http://security.ubuntu.com dapper-security/main Packages [93.3kB]
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Get: 13 http://archive.ubuntu.com dapper-backports/main Packages [13.0kB]
Get: 14 http://security.ubuntu.com dapper-security/restricted Packages [6460B]
Get: 15 http://security.ubuntu.com dapper-security/main Sources [17.9kB]
Get: 16 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get: 17 http://archive.ubuntu.com dapper-backports/universe Packages [42.8kB]
Get: 18 http://security.ubuntu.com dapper-security/restricted Sources [968B]
Get: 19 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Ign http://asher256-repository.tuxfamily.org dapper Release.gpg
Ign http://asher256-repository.tuxfamily.org ubuntu Release.gpg
Ign http://asher256-repository.tuxfamily.org dapper Release
Get: 20 http://archive.ubuntu.com dapper-backports/multiverse Packages [2508B]
Ign http://asher256-repository.tuxfamily.org ubuntu Release
Get: 21 http://au.archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Get: 22 http://archive.ubuntu.com dapper-security/main Packages [93.3kB]
Ign http://asher256-repository.tuxfamily.org dapper/main Packages
Ign http://asher256-repository.tuxfamily.org dapper/dupdate Packages
Ign http://asher256-repository.tuxfamily.org dapper/french Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/main Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/dupdate Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/french Packages
Get: 23 http://au.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://asher256-repository.tuxfamily.org dapper/main Packages
Hit http://asher256-repository.tuxfamily.org dapper/dupdate Packages
Hit http://asher256-repository.tuxfamily.org dapper/french Packages
Hit http://asher256-repository.tuxfamily.org ubuntu/main Packages
Hit http://asher256-repository.tuxfamily.org ubuntu/dupdate Packages
Hit http://asher256-repository.tuxfamily.org ubuntu/french Packages
Hit http://au.archive.ubuntu.com dapper Release
Hit http://au.archive.ubuntu.com dapper-updates Release
Get: 24 http://archive.ubuntu.com dapper-security/restricted Packages [6460B]
Get: 25 http://archive.ubuntu.com dapper-security/universe Packages [49.4kB]
Hit http://au.archive.ubuntu.com dapper/main Sources
Get: 26 http://archive.ubuntu.com dapper-security/multiverse Packages [2782B]
Hit http://au.archive.ubuntu.com dapper/restricted Sources
Hit http://au.archive.ubuntu.com dapper-updates/main Packages
Hit http://au.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://au.archive.ubuntu.com dapper-updates/main Sources
Hit http://au.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 473kB in 11s (41.8kB/s)
Failed to fetch http://ubuntu.beryl-project.org/dists/dapper/Release  Unable to find expected entry  aiglx/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Duplicate sources.list entry http://ubuntu.beryl-project.org dapper/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_dapper_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by bapoumba on 2007-01-19
> **Xummoner said:**
> 
**Failed to fetch** [http://ubuntu.beryl-project.org/dists/dapper/Release](http://ubuntu.beryl-project.org/dists/dapper/Release)  Unable to find expected entry  aiglx/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: **Duplicate sources.list entry** [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_dapper_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Looks like the beryl repo was down when you did the update (I could browse through it a minute ago). It also appears twice in your sources.list, you should just remove this line :
```
deb http://ubuntu.beryl-project.org/ dapper main aiglx
```

---

### Post by Xummoner on 2007-01-20
Oh thanks, it worked, I'm not getting the duplicate entry thing now. I don't even know why do I have those beryl repos there, I can't even manage to get it working... :P

---


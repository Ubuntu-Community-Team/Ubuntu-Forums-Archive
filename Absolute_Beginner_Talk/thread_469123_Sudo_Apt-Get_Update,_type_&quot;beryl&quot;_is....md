---
title: "Sudo Apt-Get Update, type &quot;beryl&quot; is..."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-09
```

nic@nic-desktop:~$ sudo apt-get update
E: Type 'beryl' is not known on line 132 in source list /etc/apt/sources.list
nic@nic-desktop:~$ 

```

Any suggestions?

---

### Post by ticopelp on 2007-06-09
Sounds like you have a line in your sources.list that shouldn't be there. 

```
sudo gedit /etc/apt/sources.list
```

and copy / paste the results.

---

### Post by LollYouSuckZor on 2007-06-09
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntudeb http://ubuntu.beryl-project.org feisty main
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
## Beryl repository
deb http://ubuntu.beryl-project.org/ edgy main
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main

deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://ubuntu.beryl-project.org edgy main
deb http://ubuntu.beryl-project.org feisty main
#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
#AUTOMATIX REPOS END

deb http://ubuntu.beryl-project.org/ edgy main
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb http://beryl.xglusers.de/ubuntu.beryl-project.org edgy main
deb http://media.blutkind.org/xgl edgy main
deb http://www.beerorkid.com/compiz edgy main-edgy


beryl repository
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O - | sudo apt-key add -

```

---

### Post by dbott67 on 2007-06-09
A couple of things:

1. The error is caused by a missing comment in the very last section.

```
[COLOR=Red]**# **[/COLOR][COLOR=RoyalBlue]beryl repository  *[COLOR=Purple]<---- need a comment on this line[/COLOR]*[/COLOR]
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O - | sudo apt-key add -

```

2. You've duplicated some repos a number of times.

-Dave

---

### Post by ticopelp on 2007-06-09
Okay, two things.

1) Put a # before the "beryl" in "beryl repository" at the very bottom to comment that line out.
2) the wget line should be removed. That should be copied and pasted into your terminal before you run apt-get update, not put in the sources.list. So delete that.

So it should read:

```
# beryl repository
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main
```

---

### Post by Trueno22 on 2007-06-09
At the bottom whre it says ```
beryl repository
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O - | sudo apt-key add -
``` add a # at the beginning of the word beryl

---

### Post by ticopelp on 2007-06-09
Am I wrong in thinking he should not have the "wget" command in his sources.list?

---

### Post by starcraft.man on 2007-06-09
> **ticopelp said:**
> Okay, two things.

1) Put a # before the "beryl" in "beryl repository" at the very bottom to comment that line out.
2) the wget line should be removed. That should be copied and pasted into your terminal before you run apt-get update, not put in the sources.list. So delete that.

So it should read:

```
# beryl repository
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main
```

Agreed, and one additional note. You should seriously consider cleaning up that sources list, its a mess. There is serious redundancy (multiple copies of same entry) in that list. For instance why do you have 4 or 5 seperate beryl repos... including a feisty one when your on Edgy I presume...

I'd sort what you need and get rid of rest. Thats just me though...

Edit: No, you are correct ticopelp. Wget is for downloading the key, you only do it **ONCE.** You definitely have no reason to have the entry in the sources file.

---

### Post by LollYouSuckZor on 2007-06-09
```

nic@nic-desktop:~$ sudo apt-get update
E: Type 'Failed' is not known on line 67 in source list /etc/apt/sources.list
nic@nic-desktop:~$

```

my source list:
```


deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntudeb http://ubuntu.beryl-project.org feisty main
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/Release.gpg  The HTTP server sent an invalid reply header
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/main-edgy/i18n/Translation-en_US.bz2  Bad header line
Failed to fetch http://media.blutkind.org/xgl/dists/edgy/Release  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/main-edgy/binary-i386/Packages.gz  Bad header line
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
nic@nic-desktop:~$    
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
## Beryl repository
deb http://ubuntu.beryl-project.org/ edgy main
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main

deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://ubuntu.beryl-project.org edgy main
deb http://ubuntu.beryl-project.org feisty main
#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
#AUTOMATIX REPOS END

deb http://ubuntu.beryl-project.org/ edgy main
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb http://beryl.xglusers.de/ubuntu.beryl-project.org edgy main
deb http://media.blutkind.org/xgl edgy main
deb http://www.beerorkid.com/compiz edgy main-edgy



# beryl repository
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main

```

---

### Post by LollYouSuckZor on 2007-06-09
Im not sure where to find these, but I need a source list that actually works.  

Ive had these problems for quite a while.  Can somebody post theirs? If the Beryl, etc, all works?

I'd greatly appreciate it...

---

### Post by ticopelp on 2007-06-09
Edit: Wrong Ubuntu version

---

### Post by starcraft.man on 2007-06-09
> **LollYouSuckZor said:**
> Im not sure where to find these, but I need a source list that actually works.  

Ive had these problems for quite a while.  Can somebody post theirs? If the Beryl, etc, all works?

I'd greatly appreciate it...

[This one from Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories") works as well... you need to be a lot more careful what you add to your sources list. It's an important file and you should try your best to keep it clean. Oh and if you don't readd the automatix lines I assume your gonna break that... thats up to you though, I don't recommend the program but to each his own.

---

### Post by LollYouSuckZor on 2007-06-09
I need a 6.10 source list...

---

### Post by ticopelp on 2007-06-09
> **LollYouSuckZor said:**
> I need a 6.10 source list...

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories)

There's also the Source-O-Matic: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Though I haven't used that, personally.

---

### Post by starcraft.man on 2007-06-09
> **LollYouSuckZor said:**
> I need a 6.10 source list...

I just linked you to an Edgy list... just add the Beryl repos at the end. Take more care with your list in future...

---

### Post by LollYouSuckZor on 2007-06-09
Yay. :) It's working now.

I still dont understand why Beryl freezes my computer whenever I enter it.  

Processor: AMD Sempron(TM) Processor 3000+
Avaliable Disk Space:  30.4 GB
1.80 GHz
Nvidia Geforce 5200 video card

---


---
title: "Automatix2 problem"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Mr.Kuchinawa on 2007-05-10
I'm encountering a most strange problem. When I try to start automatix2, It says that it is only for edgy. But I am sure that I should be for feisty since it worked before. 


What to do?

---

### Post by Wiebelhaus on 2007-05-10
you downloaded the wrong version.

From:
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)



Ubuntu 7.04 (Feisty i386)

[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb)
Ubuntu 7.04 (Feisty AMD64)

[http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/automatix2_1.1-4.3-7.04feisty_amd64.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/automatix2_1.1-4.3-7.04feisty_amd64.deb)
Ubuntu 6.10 (Edgy i386)

[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-4.5-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-4.5-6.10edgy_i386.deb)
Ubuntu 6.10 (Edgy AMD64)

[http://www.getautomatix.com/apt/dists/edgy/main/binary-amd64/automatix2_1.1-4.1-6.10edgy_amd64.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-amd64/automatix2_1.1-4.1-6.10edgy_amd64.deb)
Ubuntu 6.06 (Dapper i386)

[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-4.1-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-4.1-6.06dapper_i386.deb)
Ubuntu 6.06 (Dapper AMD64)

[http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/automatix2_1.1-4.1-6.06dapper_amd64.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/automatix2_1.1-4.1-6.06dapper_amd64.deb)

---

### Post by tgrisier on 2007-05-10
> **Mr.Kuchinawa said:**
> I'm encountering a most strange problem. When I try to start automatix2, It says that it is only for edgy. But I am sure that I should be for feisty since it worked before. 


What to do?

Have you tried this link --> [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) then just click on the Feisty link.  Should take you right to a link for the .deb you need.

---

### Post by ikonia on 2007-05-10
better still - don't use automatix, its not an ubuntu product and makes it harder to support your system.

---

### Post by Mr.Kuchinawa on 2007-05-10
> **sx66gns said:**
> you downloaded the wrong version.

No, I haven't. I'm using feisty i386 and it worked untill recently.

---

### Post by taurus on 2007-05-10
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Mr.Kuchinawa on 2007-05-10
```
 simen@simen-laptop:~$ cat /etc/apt/sources.list


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://no.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://wine.lowvoice.nl/apt edgy main

deb http://dl.google.com/linux/deb/ stable non-free

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse #Added by software-properties

deb http://ubuntu.beryl-project.org/ edgy main
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
#AUTOMATIX REPOS END
 
```

I can see that edgy is mentioned there. But I'm sure that I have the feisty version installed. When I try to install the feisty version, it says: that a newer version is already installed..

---

### Post by V-600 on 2007-05-10
I think I have the same problem as you (of course the cause could be different)

I had 6.10 installed with automatix2, used the update manager to upgrade to 7.04. When I first tried to use automatix2 it started and recognised version 7.04. Since a few days ago it only states that it is the wrong version.

I will let you know if I figure out how to solve the problem. Have you tried uninstalling it and reinstalling.

---

### Post by Najand on 2007-05-10
> **Mr.Kuchinawa said:**
> ```
 simen@simen-laptop:~$ cat /etc/apt/sources.list


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://no.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://wine.lowvoice.nl/apt edgy main

deb http://dl.google.com/linux/deb/ stable non-free

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse #Added by software-properties

deb http://ubuntu.beryl-project.org/ edgy main
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
#AUTOMATIX REPOS END
 
```

I can see that edgy is mentioned there. But I'm sure that I have the feisty version installed. When I try to install the feisty version, it says: that a newer version is already installed..

You sources.list is for edgy not for faisty change all "edgy" words to fesity or just replace it with the following:
```

#Ubuntu official repositories

deb http://no.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

deb http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://no.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty universe

deb http://no.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://no.archive.ubuntu.com/ubuntu/ feisty-proposed restricted main universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-proposed restricted main universe multiverse

#Wine on the lowvoice.nl
deb http://wine.lowvoice.nl/apt feisty main

# Automatix Repositories
deb http://www.getautomatix.com/apt feisty main

# Google Repositories
deb http://dl.google.com/linux/deb/ stable non-free

# Canonical Commercial Repositories
deb http://archive.canonical.com/ubuntu feisty-commercial main

# Beryl Repositories
deb http://ubuntu.beryl-project.org/ feisty main

```

---

### Post by taurus on 2007-05-10
All I can say is your /etc/apt/sources.list is a big mess!  ](*,) 

You have both automatix repos for edgy and feisty.  Personally, I would get a clean one and forget about automatix altogether.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 

```

```
sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Sef on 2007-05-10
> I can see that edgy is mentioned there. But I'm sure that I have the feisty version installed. When I try to install the feisty version, it says: that a newer version is already installed..

Automatix seems to change users source list at times.  This is the second time in the past few days that I have encountered this situation.  The other time, it changed Feisty source list to Breezy source list.

---

### Post by Najand on 2007-05-10
> **Sef said:**
> Automatix seems to change users source list at times.  This is the second time in the past few days that I have encountered this situation.  The other time, it changed Feisty source list to Breezy source list.

I have seen people complaining about it a few months ago. Sef is right. I tried to clean your own sources.list but  better to get a nice new sources.list and forget about automatix at all.

---

### Post by Saphira on 2007-05-10
"Automatix is a waste of your time and energy. Refer to these sites for more formalized documentation -- [http://wiki.ubuntu.com](http://wiki.ubuntu.com) [http://ubuntuguide.org](http://ubuntuguide.org) [http://doc.gwos.org](http://doc.gwos.org) for better help. Automatix might cause your system to break or make upgrading your system later difficult. With Feisty most of the stuff youd use automatix to install is already a one click install either via add/remove applications or by referal to one of the above sources."

---

### Post by mstlyevil on 2007-05-10
> **Sef said:**
> Automatix seems to change users source list at times.  This is the second time in the past few days that I have encountered this situation.  The other time, it changed Feisty source list to Breezy source list.

Automatix is version specific and each deb only contains the sources for that particular version of Ubuntu. Also Automatix does not touch the default Ubuntu sources. It only adds the Multiverse and Universe for that particular version of Ubuntu only if the user has not uncommented those sources. It also adds the getautomatix repo and the wine repo if that is selected. No version of Automatix currently even contains sources for breezy so this problem was likely user error.

---

### Post by mstlyevil on 2007-05-10
Here is what you need to do. You installed both fiesty and edgy Automatix and the sources list reflects that. Here is how you clean it up. Just remove this section of your sources.list and fire up Automatix. Make certain that you have the correct version of AX installed first before doing this.


Just remove completely this section 

```
#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://wine.lowvoice.nl/apt edgy main

deb http://dl.google.com/linux/deb/ stable non-free

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse #Added by software-properties

deb http://ubuntu.beryl-project.org/ edgy main
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
#AUTOMATIX REPOS END
```

Then afterwards do this:

```
sudo apt-get update
```

In the future before upgrading from one version of Ubuntu to another just fire up Automatix and remove AX sources by selecting File -> Remove Automatix Repos before the upgrade.

---

### Post by Najand on 2007-05-10
> **mstlyevil said:**
> Here is what you need to do. You installed both fiesty and edgy Automatix and the sources list reflects that. Here is how you clean it up. Just remove this section of your sources.list and fire up Automatix. Make certain that you have the correct version of AX installed first before doing this.


Just remove completely this section 

```
#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://wine.lowvoice.nl/apt edgy main

deb http://dl.google.com/linux/deb/ stable non-free

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse #Added by software-properties

deb http://ubuntu.beryl-project.org/ edgy main
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
#AUTOMATIX REPOS END
```

Then afterwards do this:

```
sudo apt-get update
```

In the future before upgrading from one version of Ubuntu to another just fire up Automatix and remove AX sources by selecting File -> Remove Automatix Repos before the upgrade.

What is the point to have the ubuntu repositories on the main server while he/she already has the Norway Mirrors... It just make the apt-get update slower?
Also, the google (deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free) has been dead for a while...

---

### Post by mstlyevil on 2007-05-10
> **Najand said:**
> What is the point to have the ubuntu repositories on the main server while he/she already has the Norway Mirrors... It just make the apt-get update slower?
Also, the google (deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free) has been dead for a while...

This user obviously upgraded Edgy to Feisty. The Google Source is no longer included in Automatix.

We use the main server simply because some of the local mirrors are slow to keep updated with the current packages.

---


---
title: "I give up.  Again."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-09
I cant install beryl on GNOME.
My sudo apt-get update dosen't work anymore.
I cant get my sources list to fix. 
I cant install any themes to make using GNOME or KDE any better.
I cant go back to XP.


Great.

---

### Post by Rocket2DMn on 2007-06-09
Sounds like a lot of visual stuff.  Can you tell us what video card you have and some other specs about your computer?

---

### Post by LollYouSuckZor on 2007-06-09
I dont know how to check my specs, and my video card is

Nvidia Geforce 5200

---

### Post by zvacet on 2007-06-09
Replace your source list with this one

[http://easylinux.info/wiki/Ubuntu:Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Edgy#How_to_add_extra_repositories")

I don´t use Beryl,but I´m sure you will find something helpfull on this forum.

---

### Post by logicalmind on 2007-06-09
> **LollYouSuckZor said:**
> I cant install beryl on GNOME.
My sudo apt-get update dosen't work anymore.
I cant get my sources list to fix. 
I cant install any themes to make using GNOME or KDE any better.
I cant go back to XP.


Great.

You might want to start out by just relaxing a bit. You sound tense. Remember when you were little and you rode that bike with training wheels? It was so easy, you couldn't fall. But you also couldn't ride very fast and you couldn't jump that jump. Think of windows as a bike with training wheels. It's going to be easy to use, but it isn't going to take you very far. Linux is like the bike without training wheels. Yeah, you're gonna fall a few times after taking off those training wheels. But once you hit that "Aha!" moment, you will be in your glory. You're gonna have to learn this stuff and it's gonna take time and effort on your part. The fastest way to learn is actually to break stuff. You're on your way to freedom from training wheels. Every time you break something, realize that you're learning something.

---

### Post by Rocket2DMn on 2007-06-09
OK, so the most important thing sounds like the sudo apt-get update
What output does it give in terminal when you try that command?

---

### Post by LollYouSuckZor on 2007-06-09
```
ic@nic-desktop:~$ sudo apt-get update
Password:
E: Type '/etc/apt/sources.list' is not known on line 1 in source list /etc/apt/sources.list
nic@nic-desktop:~$

```

and I cant even open my sources list to change it.

---

### Post by LollYouSuckZor on 2007-06-09
> **logicalmind said:**
> You might want to start out by just relaxing a bit. You sound tense. Remember when you were little and you rode that bike with training wheels? It was so easy, you couldn't fall. But you also couldn't ride very fast and you couldn't jump that jump. Think of windows as a bike with training wheels. It's going to be easy to use, but it isn't going to take you very far. Linux is like the bike without training wheels. Yeah, you're gonna fall a few times after taking off those training wheels. But once you hit that "Aha!" moment, you will be in your glory. You're gonna have to learn this stuff and it's gonna take time and effort on your part. The fastest way to learn is actually to break stuff. You're on your way to freedom from training wheels. Every time you break something, realize that you're learning something.

Riding a bike was alot easyer..

---

### Post by Rocket2DMn on 2007-06-09
> **zvacet said:**
> Replace your source list with this one

[http://easylinux.info/wiki/Ubuntu:Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Edgy#How_to_add_extra_repositories")

I don´t use Beryl,but I´m sure you will find something helpfull on this forum.

Give that a try and then fill us in.  If that works, do your updates, then we can move onto the other stuff.

---

### Post by LollYouSuckZor on 2007-06-09
I cant open my sources list. -.- It's.. Im not sure

---

### Post by Rocket2DMn on 2007-06-09
What command are you using to open the sources.list file and what output do you get in terminal?

---

### Post by logicalmind on 2007-06-09
> **LollYouSuckZor said:**
> I cant open my sources list. -.- It's.. Im not sure

Type:

cat /etc/apt/sources.list

and tell us the result

---

### Post by LollYouSuckZor on 2007-06-09
> **logicalmind said:**
> Type:

cat /etc/apt/sources.list

and tell us the result

```



/etc/apt/sources.list

sudo apt-get update

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
$ wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
$ wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
$ wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
nic@nic-desktop:~$      


```

---

### Post by Rocket2DMn on 2007-06-09
Why does it say "sudo apt-get update" inside the file?  Did you add that at some point?

---

### Post by Outrunner on 2007-06-09
Assuming you're using KDE as you stated in your profile,
```

kdesu kate /etc/apt/sources.list
```

You need to remove those lines
```

/etc/apt/sources.list

sudo apt-get update
```

---

### Post by LollYouSuckZor on 2007-06-09
> **Rocket2DMn said:**
> Why does it say "sudo apt-get update" inside the file?  Did you add that at some point?

Me, being my noobish self. Yeah.

---

### Post by LollYouSuckZor on 2007-06-09
> **Outrunner said:**
> Assuming you're using KDE as you stated in your profile,
```

kdesu kate /etc/apt/sources.list
```

You need to remove those lines
```

/etc/apt/sources.list

sudo apt-get update
```

Im actually using GNOME right now

---

### Post by Outrunner on 2007-06-09
> **LollYouSuckZor said:**
> Im actually using GNOME right now

Then you'll need to use ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by LollYouSuckZor on 2007-06-09
Okay, Two lines removed

---

### Post by Rocket2DMn on 2007-06-09
> **LollYouSuckZor said:**
> Okay, Two lines removed

The output change when you try to run update?

---

### Post by LollYouSuckZor on 2007-06-09
> **Rocket2DMn said:**
> The output change when you try to run update?


```

nic@nic-desktop:~$ sudo apt-get update
E: Type '$' is not known on line 130 in source list /etc/apt/sources.list
nic@nic-desktop:~$

```

---

### Post by logicalmind on 2007-06-09
> **LollYouSuckZor said:**
> ```

nic@nic-desktop:~$ sudo apt-get update
E: Type '$' is not known on line 130 in source list /etc/apt/sources.list
nic@nic-desktop:~$

```

Remove the last 3 lines in the file as well. The ones with wget in them.

---

### Post by Outrunner on 2007-06-09
OK, replace your sources file with this one(I removed the $'s)

NVM, replace with this... I only removed the $'s.. oops

 
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
```

---

### Post by LollYouSuckZor on 2007-06-09
> **Outrunner said:**
> OK, replace your sources file with this one(I removed the $'s)

 
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
 wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
 wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
 wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

Umn..

---

### Post by Rocket2DMn on 2007-06-09
It looks like you copied those lines from a website. 
The "$" sign is often used to represent a command to be put into a terminal, you don't actually include it.

---

### Post by LollYouSuckZor on 2007-06-09
Sudo apt-get update works :)!

---

### Post by Outrunner on 2007-06-09
Sorry, Replace it again with what I wrote above(I edited again)

---

### Post by Rocket2DMn on 2007-06-09
> **LollYouSuckZor said:**
> Sudo apt-get update works :)!

GREAT! SUCCESS!
Let the updates run, then get back to us.

---

### Post by LollYouSuckZor on 2007-06-09
updates done.

Next problem...

To get BERYL to work ONCE AND FOR ALL.

I dont know much about packages and what not.

Im dieing to have beryl.

How do I check my specs to see if I can handle it..

---

### Post by logicalmind on 2007-06-09
> **LollYouSuckZor said:**
> updates done.

Next problem...

To get BERYL to work ONCE AND FOR ALL.

I dont know much about packages and what not.

Im dieing to have beryl.

How do I check my specs to see if I can handle it..

1. What processor do you have?
2. How much memory on your video card?
3. How much memory on your system?

---

### Post by LollYouSuckZor on 2007-06-09
> **logicalmind said:**
> 1. What processor do you have?
2. How much memory on your video card?
3. How much memory on your system?

I have about 28GB..
Memory card: is 128 I believe..

Processor... It's whatever came with my HP a1203w

---

### Post by LollYouSuckZor on 2007-06-09
Base processor
Sempron 3000+ 1.8 GHz:

    *
      1600 MT/s (Mega Transfers/second)
    *
      Socket 754

---

### Post by Rocket2DMn on 2007-06-09
There are many guides to setting up Beryl.  I use an ATI card in Feisty, so I can't give you the tutorial I used, but if you google *beryl nvidia kubuntu edgy* you should get some good hits.  Just make sure your card is compatible with whatever drivers you decide to use.  I'll have a quick look for tutorials, but you can check out what looks good, too, you know your hardware and comp better than I do.

---

### Post by LollYouSuckZor on 2007-06-09
> **Rocket2DMn said:**
> There are many guides to setting up Beryl.  I use an ATI card in Feisty, so I can't give you the tutorial I used, but if you google *beryl nvidia kubuntu edgy* you should get some good hits.  Just make sure your card is compatible with whatever drivers you decide to use.  I'll have a quick look for tutorials, but you can check out what looks good, too, you know your hardware and comp better than I do.

Problem: I've tried to install it several times, one leading to a massive crash..

I have NO IDEA! where to start.
I was even trying to get somebody to remote desktop me.. to check it out.

---

### Post by Rocket2DMn on 2007-06-09
I think there is probably better support if you have Feisty, but i've never had or used an NVIDIA card.   Then again, I never did a troubleshoot on sources.list either, but it gets more complicated with drivers and video cards.  I think you just need to spend some time googling around and browsing these forums and checking that your vid card is supported and problems other people have had.
I've pretty much done what I can, not having experience with NVIDIA, Beryl just either works or it crashes X.  Finding the right guide is the key, so I wish you luck.
Just don't forget our favorite command
```
sudo dpkg-reconfigure xserver-xorg
```
This, of course, is typically run when X crashes and you just have a command prompt.
Good luck, buddy!

---

### Post by LollYouSuckZor on 2007-06-09
Im not even going to try.   Without help from somebody whos done this before.. Theres no way I'll do it right.

Bleh.  It there at least anyway, or does anyone know how to install a new theme for GNOME?

---

### Post by LollYouSuckZor on 2007-06-09
Anyway, **Thanks all of you** for the help. :)

---

### Post by logicalmind on 2007-06-09
> **LollYouSuckZor said:**
> Im not even going to try.   Without help from somebody whos done this before.. Theres no way I'll do it right.

Bleh.  It there at least anyway, or does anyone know how to install a new theme for GNOME?

As someone who has run beryl I can tell you, it's nothing special. Sure, it's cool to show off for a little while, but once that novelty factor wears off it mostly gets in the way. I turned it off after less than a day of usage. You aren't missing anything.

---

### Post by LollYouSuckZor on 2007-06-09
> **logicalmind said:**
> As someone who has run beryl I can tell you, it's nothing special. Sure, it's cool to show off for a little while, but once that novelty factor wears off it mostly gets in the way. I turned it off after less than a day of usage. You aren't missing anything.

I'll take your word.

Is there at least any themes I can download for my GNOME KDE thing.
To at least make it look better..
and MAC OSX Styled?

And how the .... are they installed..?

---

### Post by ramjet_1953 on 2007-06-09
It appears to me that you really need to do some groundwork here, before rushing into things.

If you follow this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

and just have a good read through the various menu items that are about graphics and setting-up Beryl, I'm sure that you will have a happy outcome.

Regards,
Roger :cool:

---

### Post by logicalmind on 2007-06-09
> **LollYouSuckZor said:**
> I'll take your word.

Is there at least any themes I can download for my GNOME KDE thing.
To at least make it look better..
and MAC OSX Styled?

And how the .... are they installed..?

In synaptics you should have "gnome-themes" and "gnome-themes-extras" that contain themes you can use. To change them, find your preferences in your application menu and select "Theme". 

Here are many more themes you can download.
[http://art.gnome.org/themes/metacity/](http://art.gnome.org/themes/metacity/)

---

### Post by headchange on 2007-06-09
first off you have to make sure you have your drivers installed, nvidia 5200 should be installed with 
sudo apt-get install nvidia-glx
that should get rid f your problems the only other thing you might have to do is open up /etc/X11/xorg.conf and change where it is     Driver         "nv"    to "nvidia"   before you reboot, or it might say somthing about cant start x server no screens found.
sudo gedit /etc/X11/xorg.conf
and you might want to check you source.list you got edgy and fiesty repos both on there
if your running fiesty i think beryl is in mutliunvse so you dont have to add any more repos
so  you wound just do a sudo apt-get install beryl-manager beryl emerald-themes emerald

but before that i would take out of comment out everything in your source.list that doesnt match your current running ubuntu version, then do a sudo apt-get update

---

### Post by headchange on 2007-06-09
[http://ubuntu-tutorials.com/2007/02/06/install-beryl-on-ubuntu-feisty-with-aiglx-for-nvidia-ubuntu-704/](http://ubuntu-tutorials.com/2007/02/06/install-beryl-on-ubuntu-feisty-with-aiglx-for-nvidia-ubuntu-704/)   
heres a tut for fiesty
and one for edgy
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

---

### Post by eljalill on 2007-06-20
And if you can't get beryl to work, you can still try enlightenment... some people say it's even a lot better and nicer.

---


---
title: "Installation errors Automatix2"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Diversion on 2007-05-02
when following the steps to install Automatix2 I encounter the following error when getting to the ** sudo apt-get install automatix2** command:

[B]The following packages have unmet dependencies:
  automatix2: Depends: python-gtkhtml2 but it is not installable
E: Broken packages[/B]

After searching around on the internet and this forum, I could not find any help in solving my problem. I hope someone here know what's causing this?

thnx in advance.

---

### Post by Seisen on 2007-05-02
What are you trying to install off of automatix, we can help you install the program a different way than automatix.

---

### Post by taurus on 2007-05-02
Or can you at least post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Diversion on 2007-05-02
This is what's inside the file you asked for.
I'm trying to install the program Automatix2 to easilly install multiple applications inside.
I know it's possible to do it in another way but I want to get it working by using Automatix2.

```
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse# deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu/ dapper-security universe main restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
deb http://www.getautomatix.com/apt edgy main
```

---

### Post by Jimmett on 2007-05-02
Try this. according to the manual pages -f is used to fix broxen dependancies. [PHP]sudo apt-get -f install automatix2[/PHP]

---

### Post by Diversion on 2007-05-02
Still giving the same problem:

```
$ sudo apt-get -f install automatix2
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  automatix2: Depends: python-gtkhtml2 but it is not installable
E: Broken packages

```

---

### Post by taurus on 2007-05-02
The problem is that you mix dapper repos with edgy repos and that is not a good idea.  And besides, you don't need automatix when you have medibuntu's.  

If you are running Edgy, you need to use Edgy repos only and remove the last line in /etc/apt/sources.list for automatix.

---

### Post by Seisen on 2007-05-02
The reason you keep getting that error is because its not in the dappe repo's. I found it in the  edgy and feisty repos.

---

### Post by Diversion on 2007-05-02
> **taurus said:**
> The problem is that you mix dapper repos with edgy repos and that is not a good idea.  And besides, you don't need automatix when you have medibuntu's.  

If you are running Edgy, you need to use Edgy repos only and remove the last line in /etc/apt/sources.list for automatix.

I have no idea how the 2 repos mixed, as far as I know I only used Edgy repros and installed only edgy files. Going to remove the lines from my sources.list and will look into those medibuntu's.

thanks for the help!

---

### Post by Seisen on 2007-05-02
So you don't break your computer do this to do a dist-upgrade. You can follow either way.
[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html]("http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html")

---

### Post by Diversion on 2007-05-02
thank you for the link, upgrading as we speak :)

---

### Post by oilchangeguy on 2007-05-02
after you complete the upgrade to 6.10 go to [www.getautomatix.com](www.getautomatix.com) it's very simple to install the program from their website. there's no point in using a command line to do this when the site makes it painless to install.

---

### Post by Diversion on 2007-05-02
upgrading took about half an hour and installing automatix2 worked like a charm after that!

thanks for the help guys!

---


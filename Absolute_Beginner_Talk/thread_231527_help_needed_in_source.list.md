---
title: "help needed in source.list"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by rav on 2006-08-07
i tryed 30 + times to update respotery and i get the same error
i have checked all available options in respotery but get the same error
i have a speed of 8Kbps-11Kbps.please help me

[http://in.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://in.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://in.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://in.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)



My sources.list is

## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
 deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
 deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by secret_force on 2006-08-07
well, I don't know the solution, I only know that the reason for the error is the double-dot (or whatever it's called in English) after the /Packages.gz.

One thing that surprises me though is the first line. It says
"## Uncomment the following **two lines** to fetch updated software from the network"
and there is only one line after this sentence. So maybe you should add a line "deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy main restricted" just above "deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy main restricted"

In dapper you can change the sources.list by entering in the kernel
sudo gedit /etc/apt/soureces.list <-- if you use ubuntu
sudo kwrite /etc/apt/sources.list <-- if you use Kubuntu

But I don't know too much about breezy, I switched straight to dapper, and skipped breezy. so probably the sources.list file is not saved in /etc/apt/

---

### Post by davebgimp on 2006-08-07
> **secret_force said:**
> But I don't know too much about breezy, I switched straight to dapper, and skipped breezy. so probably the sources.list file is not saved in /etc/apt/

/etc/apt/sources.list

---

### Post by Christmas on 2006-08-08
[quote=secret_force]In dapper you can change the sources.list by entering in the kernel[/quote]
In either Terminal or Konsole :)

---

### Post by rav on 2006-08-08
sir i have added the line and saves sources.list then opened synaptic package manager and pressed reload but the same error occures.


[http://in.archive.ubuntu.com/ubuntu/...6/Packages.gz:](http://in.archive.ubuntu.com/ubuntu/...6/Packages.gz:) Sub-process gzip returned an error code (1)
[http://in.archive.ubuntu.com/ubuntu/...6/Packages.gz:](http://in.archive.ubuntu.com/ubuntu/...6/Packages.gz:) Sub-process gzip returned an error code (1)

---

### Post by avtolle on 2006-08-08
To my tired eyes, looks like there is a duplicate repository. Try commenting out one of these [http://in.archive.ubuntu.com/ubuntu/...6/Packages.gz](http://in.archive.ubuntu.com/ubuntu/...6/Packages.gz) and then retry. HTH.

---

### Post by davebgimp on 2006-08-08
> **avtolle said:**
> To my tired eyes, looks like there is a duplicate repository. Try commenting out one of these [http://in.archive.ubuntu.com/ubuntu/...6/Packages.gz](http://in.archive.ubuntu.com/ubuntu/...6/Packages.gz) and then retry. HTH.

No, I see two different repos that he's getting those errors from. breezy and Breezy-updates

---

### Post by ubuntu_demon on 2006-08-08
a clean Dapper sources.list
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

---

### Post by davebgimp on 2006-08-08
> **ubuntu_demon said:**
> a clean Dapper sources.list
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

He's using Breezy.

---

### Post by cstudent on 2006-08-08
Generate a new Breezy sources.list with this tool
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)


Although, I think the problem is in the in.archive's not your sources.list.

---

### Post by ubuntu_demon on 2006-08-08
> **davebgimp said:**
> He's using Breezy.
I'm sorry. Thanks for mentioning it. I received a PM by rav asking for a link to a clean sources.list and I assumed it was for Dapper without looking.

Here's a clean Breezy sources.list (ignore the hoary to breezy upgrade instructions) :
[https://help.ubuntu.com/community/BreezyUpgradeNotes](https://help.ubuntu.com/community/BreezyUpgradeNotes)

---

### Post by rav on 2006-08-09
thanks a lot u r the best.

---

### Post by ubuntu_demon on 2006-08-09
> **rav said:**
> thanks a lot u r the best.
Did it solve your problem ?

---

### Post by rav on 2006-08-10
no it did not but i found a way . i changed this one 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

to this one

deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

---

### Post by ubuntu_demon on 2006-08-10
> **rav said:**
> no it did not but i found a way . i changed this one 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

to this one

deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
I'm glad your problem is solved then :).

---


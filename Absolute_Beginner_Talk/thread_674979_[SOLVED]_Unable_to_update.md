---
title: "[SOLVED] Unable to update"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-22
There are some updates I need to download but every time I try to it says "Not all updates can be installed" and then it gives me the option to run a partial upgrade-so I click yes, then it starts to do it but comes up saying "Unable to authenticate packages-  slang1a-utf8"

Please help it has been doing this for a while now :(

---

### Post by stoodleysnow on 2008-01-22
This sounds like a font file update. Perhaps if you do a search for this package name it will give you more info. In the mean time, don't panic. These issues often arise with updates, sometimes it is easier to wait for the next version of that package.
:-)

---

### Post by myoungf1 on 2008-01-22
Try the following command in a terminal

sudo apt-get update

sudo apt-get upgrade

Then follow the directions it gives, if any, and the failing packages should work.

---

### Post by hyper_ch on 2008-01-22
open terminal an run:

```

sudo apt-get update && sudo apt-get upgrade

```

Then you have the chance to say whether you want to install that package even if it's not authenticated.

The reason it's not authenticated is because it's in a repo from which there was no gpg key added yet to your system.

---

### Post by Fraser from Scotland on 2008-01-22
thanks everyone, I got this when I entered the codes

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by hyper_ch on 2008-01-22
why do you have ftp.debian.org as repos?

---

### Post by Fraser from Scotland on 2008-01-22
I don't know :S 
Should I not? I'm new to ubuntu so If i've got a problem and somebody tells me to do something I'll do it, unless its something obvious like the code that is in everyones sig- rm fr or something. 

Is that the problem then? if so, how do i fix it?

---

### Post by philinux on 2008-01-22
In terminal use

cat /etc/apt/sources.list

post the results

---

### Post by Fraser from Scotland on 2008-01-22
fraser@fraser-laptop:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security main restricted multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security universe

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo/
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) experimental main non-free contrib
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) experimental main non-free contrib
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main
fraser@fraser-laptop:~$

---

### Post by PmDematagoda on 2008-01-22
Open the sources list for editing using:-
```
gksudo gedit /etc/apt/sources.list
```

And uncomment the following lines by adding # in front of them, so these:-
```
 deb http://ftp.debian.org/debian/ experimental main non-free contrib
 deb-src http://ftp.debian.org/debian/ experimental main non-free contrib
 deb http://ftp.debian.org sarge main
```
look like this:-
```
#deb http://ftp.debian.org/debian/ experimental main non-free contrib
 #deb-src http://ftp.debian.org/debian/ experimental main non-free contrib
 #deb http://ftp.debian.org sarge main
```

After the changes are done, save the file and execute:-
```
sudo apt-get update
```

That should solve the problem.

---

### Post by Fraser from Scotland on 2008-01-22
Yes it Did!  thanks you everyone!!
Since I'm on the topic of updating, whenever I do sudo apt-get update this always comes up, like everytime, It doesnt seem to make a difference but maybe someone could offer some insight?

Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz)  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by PmDematagoda on 2008-01-22
Those errors could be due to a problem with the servers or it may be something to do with your internet connection. Try and ping those addresses, if the ping does not work, then they may be down.

---


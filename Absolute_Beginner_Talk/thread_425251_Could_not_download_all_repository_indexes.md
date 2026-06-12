---
title: "Could not download all repository indexes"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ligerlover123 on 2007-04-27
Seems like a lot of people are having this problem, but I couldn't find any good answers.  It won't let me update. 
It says: 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) Sub-process gzip returned an error code (1)

It won't let me upgrade to 7.04 because of this problem.  I'm brand new to Ubuntu and Linux, so I need full instructions on how to fix this.

THANKS!

---

### Post by zvacet on 2007-04-27
```
sudo aptitude update
```

If this not work just comment (put #sign in front of the line) that line

After you finish upgrade change your edgy source list with feisty

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

And after that uncomment that line and after that

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by Seisen on 2007-04-27
Actually it won't open up in the browser either. Post your source list if you know how, if not I will help you.

---

### Post by Acglaphotis on 2007-04-27
i had that problem with feisty.

What i did was:
```
sudo gedit /etc/apt/sources.list
```

Then i commented every line of the list

When your done, do:

 ```
sudo aptitude update
```

Then uncomment your repositories and do a:

 ```
sudo aptitude update
```

again.

That worked for me.

-Acgla

---

### Post by ottawa on 2007-04-27
I have a similiar problem and I am not able to get packages like phpmyadmin or php4 or php5 itself
It gave my the error E: Can't find [package name]
Those packages are in the universe repository and looking for those  packages at the website [http://packages.ubuntu.com/edgy/web/](http://packages.ubuntu.com/edgy/web/)   they "should be" available.

Are the servers too busy ? Anyone else having this ?  I tried 2 different mirror locations, de and ca for my sources.list. 

Any tips would be very appreciate as I need to install those packages. Is there maybe another way, which is easy for a Linux newbie ?

Thank's for nay help.

---

### Post by Seisen on 2007-04-27
Ottawa, had you tried using the main servers.

---

### Post by BHelts on 2007-04-27
I am having the same problem, including with the main servers.  Doesn't seem to be an isolated problem.

---

### Post by BHelts on 2007-04-27
This is the error I am getting from the main servers in synaptic

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz: Sub-process gzip returned an error code (1)

```

---

### Post by Seisen on 2007-04-27
Everybody that is having problems PM and send me your source lists. I will go through them and see if I figure out what the problem is.

---

### Post by Seisen on 2007-04-27
Hey ottawa post your source list.

---

### Post by Seisen on 2007-04-27
Try changing the http in the source list to ftp and see if that works.

---

### Post by ottawa on 2007-04-27
Hey Seisen

here my source.list
It's standard and before I checked the forum, I tried it again a few minutes ago and still can't get the packages

here the sources.list

#
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy m$


#deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy ma$

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univers$
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted uni$

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Will try ftp as you mentioned. Will post.
ottawa

---

### Post by bytesmythe on 2007-08-14
I was having a similar problem and discovered the error was not actually in my sources.list file. Try checking here:

cd /etc/apt/sources.list.d

And see if there is a file in that directory. If there is a file there, check to see if it contains a line related to the malfunctioning repository. If so, comment that line out, then try apt-get update again.

bytesmythe

---

### Post by Shogun79 on 2007-08-14
I'm having a similar problem also, here is my source.list:


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty main rest$
deb-src [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty main $

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty-updates m$
deb-src [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty-updat$

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty universe
deb-src [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty unive$

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty multiverse
deb-src [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty multi$

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## team.
deb [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty universe
deb-src [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty unive$

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty multiverse
deb-src [http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu](http://carroll.aset.psu.edu/pub/linux/distributions/ubuntu) feisty multi$

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted uni$
# deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted$

deb [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty-securit$
deb-src [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty-sec$
deb [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty-securit$
deb-src [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty-sec$
deb [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty-securit$
deb-src [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty-sec$
deb [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty-propose$
deb [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty main un$
deb [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty-updates$

Any help will be greatly appreciated.

---

### Post by joeyoung25 on 2007-08-14
I was having a similar problem with updating but i had installed iptraf and found that my box was trying to update from the main server on port 81 which doesnt exist when i changed the http: in my sources.list to ftp it fixed my problem because its obviously using port 21 instead. 

The reason why it was trying port 81 was because this box is a webserver and i had changed the apache listening port to 81 rather than 80. 

I recommend that anyone else having these problems do the same before changing anything else.

---

### Post by joeyoung25 on 2007-08-14
O yes, I forgot I also had to go to administration>software sources and specify the update server as an ftp server somewhere. I will also help you out if you can send me your sources.list

---


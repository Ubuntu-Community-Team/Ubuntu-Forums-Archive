---
title: "Updating programs"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-09-02
Hi,
   It seems like all of my 3rd party programs are not getting updated (like wine). I have the universe and multi universe repos checked off in the sources and I have also gotten all of the updates from the update manager. Is there something that I am missing to get my programs updated in the update manager? Thanks in advance.

---

### Post by dpar on 2007-09-02
What have you got listed under third party sources in synaptic?
Heres what I have.....

---

### Post by kevindubrow on 2007-09-02
Odd...I have options from 6.06:

---

### Post by dpar on 2007-09-02
That is strange......It should be Feisty stuff:confused:

---

### Post by kevindubrow on 2007-09-02
Anyone know why it is like this? I did upgrade 6.06 LTS to Feisty with a script I found on the forums.

---

### Post by kevindubrow on 2007-09-03
Can you hit "edit" on all of the Feisty sources and tell me what I need to type in? That should work, shouldn't it?

---

### Post by kevindubrow on 2007-09-11
Can anyone show me how to get all of the sources? Thanks.

---

### Post by mysticmatrix on 2007-09-11
> **kevindubrow said:**
> Odd...I have options from 6.06:

Well your fiesty update didn't go off so well. Can you point us the resource from where you got that "script"?

Also, wine repositary is not in your list, Can you provide output off this command

```
cat /etc/apt/sources.list
```

---

### Post by Maestro23 on 2007-09-11
> **mysticmatrix said:**
> Well your fiesty update didn't go off so well. Can you point us the resource from where you got that "script"?

Also, wine repositary is not in your list, Can you provide output off this command

```
cat /etc/apt/sources.list
```

Yeah, something didn't go right it sounds like.  I wonder if he saw this:[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

Says you have to first upgrade 6.06 to 6.10, then upgrade to 7.04.

---

### Post by kevindubrow on 2007-09-11
Sorry, not a script, more of a code:
$ gksu "update-manager -c"

I got it from this link:
[http://ubuntuforums.org/showthread.php?t=286599&highlight=low+screen+resolution](http://ubuntuforums.org/showthread.php?t=286599&highlight=low+screen+resolution)

And here is the output ( I went to the Wine website and got the source for it...I am still missing other sources though):

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

---


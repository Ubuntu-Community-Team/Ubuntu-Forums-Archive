---
title: "Ntfs-3g"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by CommunityZ on 2007-05-06
I tried to install NTFS-3G but refering from this tutorial [NTFS-3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") but i get this error after i type sudo apt-get install ntfs-config

albert@albert-laptop:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ntfs-config: Depends: ntfs-3g but it is not going to be installed
E: Broken packages

Can anyone help?

---

### Post by taurus on 2007-05-06
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Iarwain ben-adar on 2007-05-06
Hiya,

welcome to the forums ;)

You need to uncomment your universe repo's
```
sudo nano /etc/apt/sources.list
```

this is commented => #
so you just need to delete the # in front of those 2 lines ;)


Iarwain

---

### Post by CommunityZ on 2007-05-06
## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
#deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17
#deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17

---

### Post by Vord on 2007-05-06
I've been working with NTFS-3g and it's just screwing up really badly, I edited my fstab without backing it up and now feisty isn't automounting my secondary drive. Can somebody please post their unmodified fstab so that I can restore mine?

---

### Post by taurus on 2007-05-06
Or can you post yours?

```
cat /etc/fstab
```

---

### Post by Vord on 2007-05-06
Yeah, I don't see why not. I doubt it would help, it's not that there are errors in it, the hdb1 entry was just replaced by the NTFS-3g entry.

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=8258318d-1a92-40ee-ab89-ab4fbeb9648e / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=65679425-cea5-4e14-99c1-1535c9086dd9 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/NTFS ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by taurus on 2007-05-06
What's the output of this command then?

```
sudo fdisk -l
```

Maybe Feisty thinks it's /dev/sdb1 instead of /dev/hdb1.

---

### Post by Vord on 2007-05-06
> **taurus said:**
> What's the output of this command then?

```
sudo fdisk -l
```

Maybe Feisty thinks it's /dev/sdb1 instead of /dev/hdb1.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24320   195350368+   7  HPFS/NTFS
```

I've been using NTFS-3g since dapper, and it's always mounted to hdb1.

At this point I'm not trying to figure out what went wrong, I'm trying to fix what screwed up, namely my fstab file. I can give you any other information you may ask to see, but all I want to do is restore my fstab to it's original state so that I can see my NTFS drive again. I appreciate your help, I just feel like we're just kinda dancing around the issue.

---

### Post by taurus on 2007-05-06
What happens when you run these?

```
sudo mount -t ntfs /dev/hdb1 /media/NTFS -o nls=utf8,umask=0222
df -h
```

---

### Post by Vord on 2007-05-06
> **taurus said:**
> What happens when you run these?

```
sudo mount -t ntfs /dev/hdb1 /media/NTFS -o nls=utf8,umask=0222
df -h
```

It mounted without a hitch
```
df-h
```
Output:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             109G  3.8G  100G   4% /
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  116K 1014M   1% /proc/bus/usb
udev                 1014M  116K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/hdb1             187G  117G   70G  63% /media/NTFS
```

---

### Post by taurus on 2007-05-06
Then, maybe you want to use ntfs driver (read-only) instead of ntfs-3g for your /dev/hdb1 for now.

```
/dev/hdb1   /media/NTFS   ntfs   nls=utf8,umask=0222   0   0
```

---

### Post by Vord on 2007-05-06
Literally did that about 20 seconds before you posted. Thanks for helping with the conclusion, now if I can figure out why NTFS-3g is being such a difficult little *******

---

### Post by taurus on 2007-05-06
Just so you know.  You can write to Ubuntu (ext3) from XP with [http://www.fs-driver.org](http://www.fs-driver.org).

---


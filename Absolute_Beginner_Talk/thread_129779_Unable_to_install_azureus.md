---
title: "Unable to install azureus"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by ant80 on 2006-02-14
I followed ubuntuguide and used the command they gave. I have already installed java. It gives me an error saying it can't find the url, error 404. I am using hoary hedgehog. Azureus used to work, but the options tab wouldn't come up. So I decided to uninstall and reinstall, but I guess that was a bad idea. 

ananth@duron700:~$ sudo apt-get install azureus
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  azureus
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 4657kB of archives.
After unpacking 5280kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  azureus
Install these packages without verification [y/N]? y
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe azureus 2.3.0.2-1~5.04ubp1
  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/azureus_2.3.0.2-1~5.04ubp1_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/azureus_2.3.0.2-1~5.04ubp1_all.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ananth@duron700:~$ java -version
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)
ananth@duron700:~$

It aso seems to be a problem with the package manager. When I open Synaptic package manager and press reload, it says the repository might no longer be available and gives four lines of errors

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found

I know warty is out, but I understand that the release in April is going to be supported for longer than the standard 18 months, so I want to make do with this version until then. Please help. If you need more info, please let me know. Thanks.

---

### Post by christhemonkey on 2006-02-14
Please can you post your sources.list file.
located in /etc/apt/sources.list

---

### Post by Perfect Storm on 2006-02-14
If you use ubuntu 5.10 you should not use ubuntuguide as it's for ubuntu 5.04

If you replaced your sourcelist with 5.04 version on your 5.10 you ask for trouble.

To save your sourcelist

```
sudo gedit /etc/apt/sources.list 
```

replace it with this:

> deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

##backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## PLF test
deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free


```
sudo apt-get update
```

To install azureus:

```
sudo apt-get install sun-j2re1.5
```

Now download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.

```

cd /to/the/folder/where/you/saved/azureus
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/
sudo chown -R root:root /opt/azureus/
smeg

```

Pick **Internet** and click **New Entry**

Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png

press ok.


That should do the trick.

---

### Post by patrick295767 on 2006-02-14
Thank you again, Artificial Intelligence, for helping Linux users ! How can we reply for helping after you and have better than your post ? Accurate, precise, effective and 100% working !
You're the best, Guy ! Keep going & doing well with Ubuntu.

Greetings

Pat'

---

### Post by ant80 on 2006-02-14
Thanks Artifician Intelligence, but I actually have version 5.04 (Hoary Hedgehog), not the 5.10 (Breezy Badger). I changed the sources.list a while back when I installed the system. 

Here's my </etc/apt/sources.list> just to avoid any confusion. 
> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


---

### Post by christhemonkey on 2006-02-14
Having a quick look on the site makes me think that you need to change where it says > hoary-backports to ```
hoary-backports-staging
```

---

### Post by Perfect Storm on 2006-02-14
Okay, you can still follow the installation as I've shown of azureus.

---

### Post by ant80 on 2006-02-14
[QUOTE=christhemonkey]Having a quick look on the site makes me think that you need to change where it says  to ```
hoary-backports-staging
```[/QUOTE]

Thanks AI, it finally worked. I am running azureus now. 

Christhemonkey, I changed that entry, and when I opened the package manager, I got the following error instead of what I used to get

> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com

What does that mean?

---

### Post by stalefries on 2006-02-14
The downloads from the Ubuntu repositories are "signed" to prove thier authenticity. Aparently, the current "signature" is broken.

---


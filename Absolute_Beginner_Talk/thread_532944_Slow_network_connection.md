---
title: "Slow network connection"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by NeptuneUK on 2007-08-23
Hi there, I have just set installed Ubuntu 7.04 on a fresh hard drive on a PC but the network connection is really slow. I am unable to properly surf the web or download any updates or packages because of this.

The last time I installed Ubuntu it was using an Ubuntu Studio install disc, during the installation it had the option to automatically set up the network connection and I had no problems with it.
However, this installation was from a proper live CD installation which never presented the option to me.

The router is working fine and I have checked that the network is set to DHCP. 

I'm not sure what to do!

---

### Post by r4ik on 2007-08-23
Try,

[http://ubuntuforums.org/showthread.php?t=197419&highlight=slow+internet](http://ubuntuforums.org/showthread.php?t=197419&highlight=slow+internet)

And read Data Docters post.

Good luck !

---

### Post by NeptuneUK on 2007-08-23
Thanks I can now sort of slowly surf the web! (I'm on Ubuntu now!)

All downloads go at like 1kbps though.. I will have to wait 2 days for updates apparantly ¬_¬

---

### Post by NeptuneUK on 2007-08-23
Still no luck with the net speed.

:(

---

### Post by NeptuneUK on 2007-08-23
I have been systematically trying all of the solutions listed on this thread:

[http://ubuntuforums.org/showthread.php?t=328747](http://ubuntuforums.org/showthread.php?t=328747)

But nothing seems to work. The only reason I am so frustrated is that I installed Ubuntu Studio and everything worked fine, all of a sudden the network connection is insanely slow preventing me from effectively using the machine. :(

---

### Post by r4ik on 2007-08-23
Try,

[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

Good luck !

---

### Post by steve-shinn on 2007-08-23
Have you tried this tip ?? :-

[http://ubuntuforums.org/showthread.php?t=202838](http://ubuntuforums.org/showthread.php?t=202838)

---

### Post by NeptuneUK on 2007-08-23
The DNS thing doesnt install so thats useless, and disabling ipv6 doesnt change anything.

What can I do?

---

### Post by r4ik on 2007-08-23
Read,

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

and try again.

Good luck !

---

### Post by NeptuneUK on 2007-08-23
I cant access that web page from the PC...


This is pissing me off now, why isnt it working to begin with?

---

### Post by r4ik on 2007-08-23
Here you go,

 How to add extra repositories

    * Read #General Notes 

[edit]
Using menus

    * Choose distribution-friendly repositories. These are part of the Ubuntu distribution system. This is the recommended method. 

System-->Administration-->Software Sources

Check the repositories you think you will need (main, universe, restricted, multiverse). You probably won't need the 'sources' repository.

    * Add any third-party repositories. Such repositories are not monitored in any way. Some are quite popular, however. Use any third-party repository at your own risk. 

System-->Administration-->Software Sources-->Third-party software-->Add

Add the name of your repository. In this example, we will use Medibuntu, a popular third-party repository not affiliated with Ubuntu in any way.

APT line: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

    * Download any needed gpg keys and add them to the keylist. This key verifies the repository to your system. The Medibuntu repository (not affiliated with Ubuntu) example is shown: 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

[edit]
Manually edit sources.list

    * Manual updates are at your own risk. Mixing incompatible repositories can break your system.
    * Create a backup of your current list of sources, overwriting any previous backup. 

sudo cp -i /etc/apt/sources.list /etc/apt/sources.list_backup

    * Use a text editor (gedit or nano) to edit the sources list: 

gksudo gedit /etc/apt/sources.list

    * Edit the repositories in the sources.list similar to this template: 

    To use your local mirror you can add "cc." before archive.ubuntu.com, where cc = your country code 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse 

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
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
#deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17
#deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17


    * Download any needed gpg keys and add them to the keylist. The Medibuntu repository (not affiliated with Ubuntu) example is shown: 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

Here is another example using the Enlightenment repository (not affiliated with Ubuntu):

wget -q [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc) -O- | sudo apt-key add -

    * Refresh packages list: 

sudo apt-get update

Good luck !

---

### Post by xpod on 2007-08-23
How about Opendns?
[http://www.opendns.com/](http://www.opendns.com/)

Might help the browsing although i`m not sure about the actual dl speeds.
We`re having a fair bit of grief with our isp over bb speeds just now(as are many since the new speed upgrades) and although what i do have is still perfectly usable on one machine it`s no good for the 2 0r 3 we usually have running in the evening.

I generally do ftp/http download tests from within my isp`s own network to check my speeds though as speedtests are not the most accurate at the best of times.

---

### Post by NeptuneUK on 2007-08-23
ok.... it's working now. but i cant say why

---

### Post by r4ik on 2007-08-23
If you remember please post :)

---


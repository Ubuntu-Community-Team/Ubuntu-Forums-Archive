---
title: "I want to upgrade from Edgy 6.10 to Feisty 7.04"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by ozp on 2007-06-16
I have 6.10 and its getting older and older every day.
Its hard to find something new for 6.10 and its almost mandatory to upgrade to 7.04

The problem is that my PC must keep running because I use it to work.

Ive read people talking about bugs, breaks, system deaths, broke downloads, and all sort of problems regarding the upgrade process

I also know that the hackers, gurus, advanced and old time users now have 7.04 and some even have the new alpha. So they eventually did the upgrade.

I found these resources:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) - The official one. I think it works only if you have a clean default system

[http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html](http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html) - a very well linked tutorial. It deals with some known problems.

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall) - An alternative way to upgrade. 


My PC is a Dell notebook

I have Envy installed and I know I have to uninstall it before upgrade

I have many extra stuff and I dont have a clue about what will happend to those packages. 
What will happed when the system is upgraded but the package still for the old version
I know I have to comment out the extra repos before the upgrade, but I dont know if all those repos have feisty stuff.

I have a list of all my installed packages. If needed I can upload here.

My repos are here:

```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://seveas.theplayboymansion.net/seveas edgy-seveas all

# Upstream Wine
deb http://wine.budgetdedicated.com/apt edgy main

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse #Added by software-properties

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse #Added by software-properties

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse #Added by software-properties

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse #Added by software-properties


## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb http://medibuntu.sos-sts.com/repo/ edgy free
# deb http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
deb http://theli.free.fr/packages/ edgy listen


## Official Skype Repository
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Treviño’s Ubuntu edgy Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" software: aMule, amsn, mplayer, moto4lin, flashplugin & flashplayer (9.x)…
# Further informations: http://3v1n0.tuxfamily.org
deb http://download.tuxfamily.org/3v1deb edgy 3v1n0

## Compiz Gandalfn
deb http://gandalfn.club.fr/ubuntu edgy dev

## Debuntu
deb http://repository.debuntu.org/ edgy multiverse

## Ascher256
deb http://asher256-repository.tuxfamily.org edgy main dupdate
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate

## Beryl oficial
deb http://ubuntu.beryl-project.org/ edgy main


deb http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu edgy/
deb http://www.mclean.net.nz/debian stable contrib


```

Please tell me a safe way to upgrade.

This is my first successful linux box and now I'm using only linux.
Took me a very long time to make it work good. 

I cant afford to loose all this work.

As far as I can remember there are only somethings that are not working:

5 botom mouse - only works on firefox after changing config files

---

### Post by skymera on 2007-06-16
isnt it 

```
 sudo apt-get update
sudo aptitude upgrade
sudo aptitude dist-upgrade 
```

or do it from update manager

---

### Post by zvacet on 2007-06-16
Comment all unofficial repos like medibuntu,trevino and so on(put # in front of the line).Leave just officilal repos and upgrade with upgrade manager.Second option is to download alternate Cd and upgrade from it.

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by ozp on 2007-06-17
But is this safe?

I mean. Did a lot of people said they had success upgrading?
Did a lot of people said thay had errors?

---

### Post by zvacet on 2007-06-17
Lot of people said both.Nothing is 100% sure.That is why I give you second option(alternate Cd).In the case that upgrade fail you have Cd for fresh install.But please take my advice and use just official repos during upgrade.That way you have better chance for good upgrade.If I´m unclear in some way you say it and I will try to help you as much as I can.

You have separate home partition,do you?If not make one this way 

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by ozp on 2007-06-21
Ok! I&#314;l wait until I have a day off and try the upgrade with the official repos and with the alternate CD for a "backup" choice.

I 've seen the page for separate home. 

I have to do that also because I have a XP here and I need to grow the linux partitions because the XP is not being used anymore.

I have about 20GB free on that XP partition

Thanks for the help!

---


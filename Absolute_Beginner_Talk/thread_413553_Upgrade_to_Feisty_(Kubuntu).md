---
title: "Upgrade to Feisty (Kubuntu)"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-04-19
I need help upgrading to feisty. I've performed all the steps belows (except for#2). How do I enable edgy updates? I don't have anything like that in my source.list...

>    
1. Open the Adept Manager by going to KMenu -> System -> Adept Manager (Manage Packages).

2. In Adept -> Manage Repositories enable edgy-updates (or feisty-updates "Recommended Updates" if you are already on feisty)

3.  If you are using the Edgy KDE 3.5.6 repository, also add deb [http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/](http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/) edgy main

4. If your system is up to date, the upgrade wizard will be offered it via the Version Upgrade button. 

---

### Post by Bachstelze on 2007-04-19
What does your sources.list look like, currently ?

---

### Post by lazyrussian on 2007-04-19
Here you go:

> 
deb [http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/](http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/) edgy main 


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main 

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse 
#AUTOMATIX REPOS END

deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy universe 
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy universe 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn 
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main 
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main 
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main 
deb [http://kubuntu.org/packages/kde-356](http://kubuntu.org/packages/kde-356) edgy main 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 
deb [http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/](http://kubuntu.org/packages/kde-356-pre-feisty-upgrade/) edgy main 


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main 

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse 
#AUTOMATIX REPOS END

deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy universe 
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy universe 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn 
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main 
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main 
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main 
deb [http://kubuntu.org/packages/kde-356](http://kubuntu.org/packages/kde-356) edgy main 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 


---

### Post by richbiskit on 2007-04-19
I have the same problem! Any help would be welcome!!

---

### Post by munky-head on 2007-04-19
I have read that you can just easily upgrade by typing **update-manager -c -d** in the terminal.

---

### Post by lazyrussian on 2007-04-19
update-manager is a GNOME program. I don't if it will work for me if I install it.

---

### Post by mattack on 2007-04-19
> **lazyrussian said:**
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

looks like they are already enabled.

---

### Post by Seisen on 2007-04-19
<snip>

---

### Post by lazyrussian on 2007-04-19
> **Seisen said:**
> <snip>

Can anyone second that? I don't wanna screw my computer up if I do this...

---

### Post by dptxp on 2007-04-19
> **Seisen said:**
> Just go through and change everything from edgy to feisty except for that first entry and see what happens.

[COLOR="Red"][SIZE="4"]That is a dangerous option[/SIZE][/COLOR] :confused:

---

### Post by AusIV4 on 2007-04-19
That's the most likely way to break your system. The upgrade managers do some safety checks and fix things that are likely to cause failures.

I'm currently upgrading, all I had to do was run adept_updater and get my system up-to-date, then run adept_manager, hit "fetch list of updates" and a window popped up offering an upgrade.

Now I'm downloading my 7th of 1394 files for the installation.

I might note that I haven't had a successful system upgrade since the Breezy -> Dapper upgrade (it may just be a dapper->edgy problem, but I did that on multiple systems), so I highly recommend backing up your home directory at the very least.

---

### Post by lazyrussian on 2007-04-19
That's what I thought. Any other ideas anyone?

---

### Post by lazyrussian on 2007-04-19
That's already backed up. Damn, I need to rush off to class (in college) and I was hoping to get this to work while I was gone all day :(

ANyway! Please leave me more info if anyone can - I'll check as often as I can.

---

### Post by Seisen on 2007-04-19
Its the same damn thing that the update manager does. Its how I upgrade mine because I couldn't  get the other options to work, its your perogative.

---

### Post by Seisen on 2007-04-19
> **AusIV4 said:**
> That's the most likely way to break your system. The upgrade managers do some safety checks and fix things that are likely to cause failures.

I'm currently upgrading, all I had to do was run adept_updater and get my system up-to-date, then run adept_manager, hit "fetch list of updates" and a window popped up offering an upgrade.

Now I'm downloading my 7th of 1394 files for the installation.

I might note that I haven't had a successful system upgrade since the Breezy -> Dapper upgrade (it may just be a dapper->edgy problem, but I did that on multiple systems), so I highly recommend backing up your home directory at the very least.

The update manager and apt are the same damn thing. The only difference is the update manager is a gui. Here's a link that describes the same thing I am.

[http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html]("http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html")

---

### Post by richbiskit on 2007-04-19
I fixed it like this....

In Manage Repositories, find...

deb [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) edgy universe
 and 
deb-src [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) edgy universe

(you wont have lt.archive (unless you are in Lithuania) it will read somthing like uk or us.archive)

now change universe to multiverse, next fetch updates and you will be given the option to get a new version of Kubuntu!

Sweet

---

### Post by lazyrussian on 2007-04-19
> **Seisen said:**
> The update manager and apt are the same damn thing. The only difference is the update manager is a gui. Here's a link that describes the same thing I am.

[http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html]("http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html")

Should I just do sudo adept -c then? (I'm at a workstation computer at the moment so I can't try it)

---

### Post by Seisen on 2007-04-19
Just follow the original direction that you had because apparantly they decided to say that the method I use isn't very good.

[https://help.ubuntu.com/community/FeistyUpgradesManual]("https://help.ubuntu.com/community/FeistyUpgradesManual")

I wish they would make up their mind on which method works, because the first two options don't work all the time.

---

### Post by Detonate on 2007-04-19
These are the official instructions.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by lazyrussian on 2007-04-19
I ended up backing up my info and doing a fresh install.

Now I only have problems:

1. My Soundcard isn't recognized
2. Adept Won't Update. It keeps stalling and timing-out when I hit fetch-updates...so I can't install/uninstall anything :(

---


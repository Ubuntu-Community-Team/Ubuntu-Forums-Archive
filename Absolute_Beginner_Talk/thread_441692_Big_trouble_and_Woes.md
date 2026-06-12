---
title: "Big trouble and Woes"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-05-12
This morning when I fired-up Dapper Drake I was welcomed with this message from Package Manager:

> E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I downloaded the package;" oss-Linux_v4.o-123_i386.deb". Clicked on it and got this from Package Installer:

[IMG]http://img.photobucket.com/albums/v519/Romin_1/snapshot2.png[/IMG]

Toward the bottom it tells me to remove the file "user/lib/oss/starting then to run soundon again. This I have no idea how to do.

This has me totally up against the wall. Synaptic says it's not in the archive and needs to be installed, the installer tells me the oss crashed and needs to be re-started. How the blue blazes can you re-start something that, for all intents, does not exist any longer.

I opened Synaptic to look for it and Synaptic is EMPTY. Nothing, nada zilch. About as empty as my head now is.

I tried to install it in Root Terminal with basically the same results. Clicked GDebi and it says this is the same one that is already in there. Sheeeesh! One say do, one say don't...

Is there a way out of this mess short of deleting the partitions and starting all over again?

If there was a Hall of PC Misfortune I'd be in there somewhere.

My eternal gratitude for any assistance,

Jon

---

### Post by Romin-1 on 2007-05-13
[BUMP] Still hoping someone has a solution, please.

Jon

---

### Post by Happy_Man on 2007-05-13
Could please post the output of 
```
cat /etc/apt/sources.list
```
please?

---

### Post by Romin-1 on 2007-05-13
Here it is, Happy man:

jon@jon-desktop:~$ cat /etc/apt/sources.list

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse#AUTOMATIX REPOS END
jon@jon-desktop:~$
jon@jon-desktop:~$ cat /etc/apt/sources.list

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse#AUTOMATIX REPOS END
jon@jon-desktop:~$

---

### Post by tgalati4 on 2007-05-13
Examine the following in a terminal:

last

history

Try to determine what users and what commands were executed over the past day.

Did you perform any upgrades over the past day?  What was the uptime of the system before shutting down?  If your machine is up for months (like mine) then an upgrade done months ago won't break your system until you reboot since you are running off of the old libraries.

It could be something from Automatix that has broken OSS.  Do you need OSS?  Perhaps you can delete it completely (through synaptic) and if you don't use any apps that need OSS then you should be OK.

---

### Post by Romin-1 on 2007-05-13
Hi tagalati4,

I'm the only user and have not installed anything for several days. The machine has been through several cold boots or restarts since the last install. 

Here's the kicker; Synaptic is completely empty; nada, zilch, zero. No files at all listed. How about that?

Only installed one prog through Automatrix and that was about a month ago.

Am I having fun or what ?

Thanks for your help,

Jon

---

### Post by Happy_Man on 2007-05-13
Try making a new sources.list using [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Remember to back up your old one, first!

---

### Post by Romin-1 on 2007-05-13
Boy, oboy; no matter what I tried all I got was permission denied, needs argument, and a bunch of other reasons I forgot for not installing the repositories.

Is it possible to repair this using the Live CD or do I have to do a full install? On a full install does it overwrite this damaged one or make two more partitions?

And they thought I was crazy before,,,

Jon

---

### Post by tgalati4 on 2007-05-13
It could be a simple permissions problem.

Mine looks like:

-rw-r--r-- 1 root root 2315 2007-03-29 16:11 /etc/apt/sources.list

for a Dapper system.

The other possibility is that Synaptic itself is broken.  Report the output from the following:

sudo apt-get clean
sudo apt-get check

---

### Post by cgrahge on 2007-05-13
> **Romin-1 said:**
> This morning when I fired-up Dapper Drake I was welcomed with this message from Package Manager:



I downloaded the package;" oss-Linux_v4.o-123_i386.deb". Clicked on it and got this from Package Installer:

[IMG]http://img.photobucket.com/albums/v519/Romin_1/snapshot2.png[/IMG]

Toward the bottom it tells me to remove the file "user/lib/oss/starting then to run soundon again. This I have no idea how to do.

This has me totally up against the wall. Synaptic says it's not in the archive and needs to be installed, the installer tells me the oss crashed and needs to be re-started. How the blue blazes can you re-start something that, for all intents, does not exist any longer.

I opened Synaptic to look for it and Synaptic is EMPTY. Nothing, nada zilch. About as empty as my head now is.

I tried to install it in Root Terminal with basically the same results. Clicked GDebi and it says this is the same one that is already in there. Sheeeesh! One say do, one say don't...

Is there a way out of this mess short of deleting the partitions and starting all over again?

If there was a Hall of PC Misfortune I'd be in there somewhere.

My eternal gratitude for any assistance,

Jon
Please do the following:
```
sudo rm -f /var/lib/dpkg/info/oss-linux.postinst
sudo dpkg --remove --force-remove-reinstreq oss-linux
sudo apt-get update
sudo apt-get install oss-linux
```
This will fix apt/synaptic/Automatix etc.

---

### Post by Romin-1 on 2007-05-13
Hot Diggity Dang! Drinks all around fellas,,,

cgrahge, your suggestion worked like a charm.

Thanks again, all

Jon

---


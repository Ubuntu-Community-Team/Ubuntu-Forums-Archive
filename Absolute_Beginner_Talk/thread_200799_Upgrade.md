---
title: "Upgrade?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-06-20
I slaped Ubuntu in cuz i've been away with other projects and missed using it.

I'm getting a message to upgrade to "6.06 LTS."  When I click on the Upgrade button, the process starts but stops and I get the folowing message:

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

What does this mean? How do I correct it? And what exactly am I upgrading?

---

### Post by richbarna on 2006-06-20
You are upgrading the OS from Breezy Badger to Dapper Drake the latest offering from Ubuntu.

You have two choices :-
1. I can help you sort out your problem so that you can upgrade.
2. You can download a fresh copy of Dapper [HERE]("http://www.ubuntu.com/download")

---

### Post by georgetoon on 2006-06-20
[QUOTE=richbarna]You are upgrading the OS from Breezy Badger to Dapper Drake the latest offering from Ubuntu.

You have two choices :-
1. I can help you sort out your problem so that you can upgrade.
2. You can download a fresh copy of Dapper [HERE]("http://www.ubuntu.com/download")[/QUOTE]

Okay.:) I'll give it a shot..let's try and sort it out here.:)  thank you.:)

---

### Post by teaker1s on 2006-06-20
edit your /etc/apt/sources.list so that all there are only the offical repositories enabled. then, sudo apt-get update, and sudo apt-get dist upgrade.

---

### Post by georgetoon on 2006-06-20
[QUOTE=teaker1s]edit your /etc/apt/sources.list so that all there are only the offical repositories enabled. then, sudo apt-get update, and sudo apt-get upgrade.[/QUOTE]

I opened up /etc/apt/sources.list and not sure what the oficial repositories are. so, not sure what/how to edit.

Would unchecking

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

in repositories be essentially the same thing?  then just let the upgrade continue?



I'll do the download.)

---

### Post by fritz_monroe on 2006-06-20
I'm not certain, but wouldn't he be able to do the same thing by changing the Synaptic Repositories?  To get there, System >> Administration >> Synaptic Package Manager

Then Settings >> Repositories

The official sites are listed as official.

---

### Post by georgetoon on 2006-06-20
[QUOTE=fritz_monroe]I'm not certain, but wouldn't he be able to do the same thing by changing the Synaptic Repositories?  To get there, System >> Administration >> Synaptic Package Manager

Then Settings >> Repositories

The official sites are listed as official.[/QUOTE]

That's what I'm thinking.:)  Do I uncheck anything that does not have the word "Official" in it?

---

### Post by richbarna on 2006-06-20
Personally I would redo the sources.list 
In the terminal, copy and paste this :-

> gksudo gedit /etc/apt/sources.list

Then delete everything you see in gedit, and copy and paste this :-

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free 

It's already prepared for Dapper repositories.
Then :-

> sudo apt-get update && upgrade

And :-

> sudo apt-get dist-upgrade

---

### Post by georgetoon on 2006-06-20
[QUOTE=richbarna]Personally I would redo the sources.list 
In the terminal, copy and paste this :-



Then delete everything you see in gedit, and copy and paste this :-



It's already prepared for Dapper repositories.
Then :-



And :-[/QUOTE]


Wel, I did all that and Ubuntu is now.....dead. Well, not excactly dead...just missing, so to speak.

I don't know where I messed up. Definetly my error.
 
Here's what happened:

I did everything you insructed.   things got updated.:)  Then, I was given the option to do an update again.  I did that update. I overwrote files when asked and did not keep anything from the previous instal of Breezy.   I thought this was what Ubuntu wanted.

Well, after doing all this, it instructed me to reboot, which I did.  When it came up, it displayed nothing but a terminal prompt and message about the "gdm" being disabled. 

So, technicaly, it's still there (as Breezy Badger, I think..at least this is what it says), but it doesn't give me the desktop.  Just a login prompt.

Ah, well...I guess my next option is to just download Dapper and do a complete, clean re-install andoverwrite everything that's on the drive.

Thanks again for your help.  My apologies for messing up your very good advice.

---


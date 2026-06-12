---
title: "Synaptics wants to uninstall everything!"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-06-03
When I try to uninstall anything using synaptics it tells me that other packages will be uninstalled and it gives me a list of every package on the system.  I am not pointing at any important system files or anything.  Just Qt3, Qt4, and Automatix.  Though I have tried this and gotten the same results with each package that i say i want to uninstall it gives me the same message.  That basically everything will be uninstalled.  How can i fix this problem?

---

### Post by chameleon_789 on 2006-06-03
Have you got any broken packages in synaptic ( custom / broken )?

---

### Post by catlett on 2006-06-03
Have you uninstalled anything lately. If you uninstall something, synaptic will "clean up" the other applications that won't work any more because they depended on what you just unninstalled. So if you uninstalled something that may be it.
A way to make sure you have everything for ubuntu up to date is to use aptitude. It deals with dependencies better than apt-get . Run this ```
sudo aptitude upgrade
``` Whatever it says needs to be installed, or uninstalled, needs to be to resolve your dependecies at the moment.
 If you don't want to you can abort it. If you uninstalled something then reinstall it to stop these issues. Otherwise I don't know why this is happening.

---

### Post by Mustard on 2006-06-03
What version of Ubuntu are you running?  What is the contents of your current sources.list?

---

### Post by JNowka on 2006-06-03
I have 2 broken files, that i installed a few days ago because i don't have all of the dependencies, though several days before that I tried to uninstall the same files but had the same results.

I have not uninstalled anything, I just wanna clean up my stuff.

Breezy, waiting on dapper cd's to come in the mail. 

Sources.list:
[HTML]deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe[/HTML]

---

### Post by catlett on 2006-06-03
The problem may be that you only have your cd and 1 repository enabled as a source for synaptic. Remove the "#"s from in front of every line that begins with deb and put a # in front of deb cdrom. Then run ```
sudo aptitude update
``````
sudo aptitude upgrade
``` That will most likely take care of everything.
FYI... A "#" in front of a line of text wil make that line a comment and therefore the line will be ignored by synaptic. As you can see you have a # in front of every line but 2

P.S. That mustard is so g----n smart.:D

---

### Post by JNowka on 2006-06-03
I don't even know why one repository is enabled, the linux computer cant even connect to the internet.  I download everything i need from packages.ubuntu.com the hard way, one at a time.  Ill have to put a # infront of that.

---

### Post by Mustard on 2006-06-03
[QUOTE=JNowka]I don't even know why one repository is enabled, the linux computer cant even connect to the internet.  I download everything i need from packages.ubuntu.com the hard way, one at a time.  Ill have to put a # infront of that.[/QUOTE]

The plot thickens. :)  What happens after you run an apt-get update now, with just the CD ROM listed in your sources.list?

Are all your packages you have downloaded for the same version of Ubuntu?  ie are you mixing breezy and dapper packages?

What is the exact conflict that Synaptic is giving which is causing all packages to be uninstalled?  Normally it would say which package is causing the conflict.

---

### Post by JNowka on 2006-06-03
It just keeps saying done, without error.

None of the packages are for dapper.  I make sure that the combobox always says breezy before I search. 

It shows no conflict, I just keep marking Automatix for uninstall because I know it isnt a dependency to anything and it doesn't have dependencies.  And it shows that to remove one you have to remove them all.

---


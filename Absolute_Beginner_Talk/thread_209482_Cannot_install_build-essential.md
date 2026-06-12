---
title: "Cannot install build-essential"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-07-05
Hi,

I am trying to install build-essential on Dapper.

I get the following error from Synaptic :

build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: gcc but it is not going to be installed
 Depends: g++ but it is not going to be installed



If I try to install libc6-dev I get :

ibc6-dev:
  Depends: libc6 (=2.3.5-1ubuntu12.5.10.1) but 2.3.6-0ubuntu20 is to be installed


I cannot find libc6 in the standard repositories (I even looked in multiverse)

Has anyone got any ideas what I need to do to install build-essential or equivalent.

Thanks,

Adam

---

### Post by richbarna on 2006-07-05
Ok you need to allow universe and multiverse in the repos.
You can either do it in synaptic or edit your sources.list.
If you choose the second method I can post a sources list for you to copy and paste.

Once you've done that, open the terminal and copy and paste this command :-
> sudo apt-get update && sudo apt-get upgrade

This will refresh the sources/repository. Then go for build-essential again.

Post back if you need more help ;)

---

### Post by adam s on 2006-07-05
Hi,

Thanks for the reply, but I still get the same error. As I already had universe and multiverse in the repos..... I even added backports for this install (just in case)

Thanks,

Adam.

---

### Post by lamego on 2006-07-05
Your repositories must be pointing to the wrong distro version, probably breezy.

---

### Post by adam s on 2006-07-05
How do I repair this....

P.S. This was a clean install from a Dapper CD (not an upgrade)

Thanks,

Adam.

---

### Post by Sef on 2006-07-05
Could you post your repositories, so they could be checked.

---

### Post by tommcd on 2006-07-05
Sorry if this sounds like a dumb question, but are you sure you have universe/multiverse repos enabled? And reloaded/refreshed after enableing them.
I can find many different versions of libc6 in my synaptic.

---

### Post by richbarna on 2006-07-05
I think that it's the repos too,
Try this :-
In your terminal type
> gksudo gedit /etc/apt/sources.list
when it opens the gedit editor, delete everything and then copy and paste my one :-
Save and Exit
> 
##Ultimate Dapper Sources List

##Standard Ubuntu Packages
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Automatix (PGP Key: 521A9C7C)

##deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

##Wine

##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
##deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

##Seveas Packages Not Included In Ubuntu

##deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas extras
##deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas extras

##Cipherfunk multimedia packages (PGP key: 33BAC1B3)

##deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
##deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

##Dapper PLF

##deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
##deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free









Now do the 
> sudo apt-get update && sudo apt-get upgrade

---

### Post by adam s on 2006-07-05
Thanks Richbarna,

That seemed to solve the problems.....

I don't know what was wrong with my repros as this was a clean install.....

Thanks,

Adam

P.S. Tommcd - your question isn't stupid - it is always the simple things that are missed out....But I had refreshed my repros after adding multiverse and universe....

---

### Post by richbarna on 2006-07-05
[QUOTE=adam s]Thanks Richbarna,

That seemed to solve the problems.....

I don't know what was wrong with my repros as this was a clean install.....

Thanks,

Adam

P.S. Tommcd - your question isn't stupid - it is always the simple things that are missed out....But I had refreshed my repros after adding multiverse and universe....[/QUOTE]

No problem, glad it's all ok now. And you're right, the only stupid question is the one that isn't asked.

---

### Post by mahoodlum on 2006-07-20
Ok I did this too hoping that it would solve the same problem, however, the repos still have Libc6 2.4 and not 2.3.6 

I am at a loss for what to do, please help

This is the error

> $ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages

---

### Post by OmahaVike on 2007-05-30
boy, this thread has aged!  finally am finding the problem here.  i'm in the same boat as mahoodlum.

after examining a thread of dependencies, i'm finding that my libc6 is currently at version **2.4-1ubuntu12** and i need version **2.3.6-0ubuntu20.4** to install build-essential (or the thread of dependencies, anyway).

so, i go into synaptic and attempt to force the old version.  upon doing so, synaptic warns me that it will uninstall the kitchen sink, the bathtub and all plumbing.  just a quick glance at all of the uninstalls, and i quickly discover that this is a road i do _not_ wish to traverse.

anyone have an idea of how we can roll back versions of libc6 without a minor thermonuclear detonation?

thanks for any and all help.

---


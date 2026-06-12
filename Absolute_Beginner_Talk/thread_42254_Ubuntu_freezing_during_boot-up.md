---
title: "Ubuntu freezing during boot-up"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by Run Away on 2005-06-16
EDIT: See new post, problem has re-occured.

---

### Post by N'Jal on 2005-06-16
Have you upgraded your kernel recently?

---

### Post by poofyhairguy on 2005-06-16
[QUOTE=Run Away]XP took a crap on us, so we now boot up in linux only.
We have 5 options I think when booting up:

XP Home
Ubuntu 1
Ubuntu 1 (safe mode)
Ubuntu 2
Ubuntu 2 (safe mode)

I always chose the Ubuntu 1 (not sure of the real name, it's long). Problem is, today I went to boot up Ubuntu 1, and it always freezes at the point where it says:

Loading modules...

Luckily, Ubuntu 2 works, and I am using that now. I'm wondering what I should do to fix it?
I'm completely clueless when it comes to linux.
Thanks.[/QUOTE]


try this command in the terminal:

sudo apt-get install linux-686

and reboot. Tell me what happens.

---

### Post by Run Away on 2005-06-16
[QUOTE=N'Jal]Have you upgraded your kernel recently?[/QUOTE]
Not sure exactly what that means, but yes I did update all the things the automatic update thing told me to.

PHG, I'll try that now.

---

### Post by Run Away on 2005-06-16
Okay, I did that and the boot up list now reads

XP Home
Ubuntu, Kernel 2.6.10-5-k7
Ubuntu, Kernel 2.6.10-5-k7 (safemode)
Ubuntu, Kernel 2.6.10-5-686
Ubuntu, Kernel 2.6.10-5-686 (safemode)
Ubuntu, Kernel 2.6.10-5-386
Ubuntu, Kernel 2.6.10-5-386 (safemode)
Ubuntu, Kernel memtest86+

Startup works now when selecting Ubuntu, Kernel 2.6.10-5-k7 (the one I think I was used to using - I had always chosen the one right below XP)

Thanks guys

---

### Post by Run Away on 2005-07-07
Bump to top-

It's doing the same thing now, but now all selections don't work when starting up.
I just am lucky it somehow worked just now.

Is there any way to fix this re-ocurring problem?
I also get "Failed to initialize HAL" errors when logging into other profiles too.

It all ties in with the fact that Ubunbtu sometimes does not recognize the CD-RW drive. It shows that it's there, but it's name is no longer CD-RW, but CR-ROM 1 or something similar. When booting up in safemode it always hangs up at

Loading modules...
             -CD-RW-

How can I fix this?

---

### Post by Run Away on 2005-07-07
When trying to fix it the way it was fixed the first time, I get this:

> ben@family:~$ sudo apt-get install linux-686
Password:
Reading package lists... Done
Building dependency tree... Done
linux-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
ben@family:~$
ben@family:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by poofyhairguy on 2005-07-07
[QUOTE=Run Away]When trying to fix it the way it was fixed the first time, I get this:[/QUOTE]

First of all, do this please:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Your sources.list is tainted. That will fix things quickly. Then do this:

sudo apt-get update

Then do 

sudo apt-get install linux-686 

(install:

linux-686-smp

if you have hyperthreading or two CPUS).

---

### Post by Run Away on 2005-07-07
Thanks for the quick reply. However, I do not have a section similar to what it shows in the guide.
This is what my sources.list reads

> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted 

Should I copy all of step #4 in the link you provided for me and replace all of it with that?
Thanks again.

---

### Post by Run Away on 2005-07-07
This is what it reads now:
> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted 

It's not the same as what is listed in step #4 there, but I think this is what it is supposed to be once fixed, correct?

> ## Uncomment the following two lines to fetch updated software from the network
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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted



Is that correct?

---

### Post by Run Away on 2005-07-07
Okay, I changed my sources.list and put in only what is shown in the guide, nothing else, and did the updates, then I did the "sudo apt-get install linux-686" and it tells me I have the newest version already.

Is that it? It's fixed now? I don't want to try to restart in fear that it won't boot again.

---

### Post by Run Away on 2005-07-11
Well after a few days of running perfectly it did it again.

Is there some sort of fix?
Everything is updated, every kernal is the newest version, I've done all the things mentioned in this thread, why does it keep comming back?

---

### Post by crashd on 2005-07-26
[QUOTE=Run Away]Well after a few days of running perfectly it did it again.

Is there some sort of fix?
Everything is updated, every kernal is the newest version, I've done all the things mentioned in this thread, why does it keep comming back?[/QUOTE]
I have your same problem and I would want to resolve. :(
Some times jam also in "hotplug"

---


---
title: "To install from repos or not to install from repos, that is the question."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Ryuki_NdranC on 2008-04-19
Ok, I had to install Gusty Gibon cause:

1. I'm still a n00b
2. Several ppl advice to wait 4 weeks after release to upgrade
3. Got a problem with the partition on the beta (:confused:)

Anyway, I'm back to Gusty and i was wondering something, since Gusty repos (apparently) have older version of the current programs, what do you think is the best to do in my case? install from repos, or install from the internet?

I know repos are so much easier, but its worth it? I mean, if i'm going to have older versions of everything, does that mean "they" are forgeting about gusty respos?

so what (in your humble opinion) think i should consider the most? wait 24 april and upgrade? Stick with old Gusty and install from internet or go for the repos no matter what?

thx in advance. I have confirm some applications to be older in the repos supposedly because they are more "stable". how much truth is in that?

Thx in advance.

---

### Post by lswest on 2008-04-19
you can enable the backport repositories, which will install the newest software available from the repos, such as firefox 3 beta 5, etc. etc.  Maybe have a look there first?

to enable it go to system-->administration-->software sources, under the "updates" tab, choose "gutsy-backports" and proposed too if you want.

---

### Post by Siph0n on 2008-04-19
If your are happy with not having the latest versions of software, than use repos :) My suggestion is to check the new features of software, and if you need/want that new feature than install it yourself, but if you wouldn't use that new feature than use the repos for the older version without that new feature :)

---

### Post by Ryuki_NdranC on 2008-04-19
> **lswest said:**
> you can enable the backport repositories, which will install the newest software available from the repos, such as firefox 3 beta 5, etc. etc.  Maybe have a look there first?

to enable it go to system-->administration-->software sources, under the "updates" tab, choose "gutsy-backports" and proposed too if you want.

I have activated the backports, i'm now updating the gusty (just installed right now), but when i chose with synaptic or apt-get (for example) sudo apt-get install firefox that install the newest? (3b5) or just 2.0???

The same with most programs?

Thx you both for the answers.

---

### Post by oldos2er on 2008-04-19
"but when i chose with synaptic or apt-get (for example) sudo apt-get install firefox that install the newest? (3b5) or just 2.0???"

 It will install the one in the repositories, 2.0.x.x something. If you want 3b5, you need to download it from mozilla.org.

---

### Post by Tatty on 2008-04-19
You can find out what is in the backports repo by checking here [http://packages.ubuntu.com/gutsy-backports/]("http://packages.ubuntu.com/gutsy-backports/")

After Ubuntu release, the repos are frozen so the only updates made to them are security patches, or if a serious bug is found which has a simple fix.  If they keep updating the software all the time then it increases the chances of breakages.

The big question, as has already been mentioned, is do you need the latest version?  Most of the time a new version of software offers very little extra compared to the last version.  It is very rare i find that I need a version of software that isnt in the repos.  Its usually much easier to stick to the repos - but its your computer and you have the freedom to set it up however you want, its just down to what suits you best :)

---

### Post by Ryuki_NdranC on 2008-04-19
> **oldos2er said:**
> "but when i chose with synaptic or apt-get (for example) sudo apt-get install firefox that install the newest? (3b5) or just 2.0???"

 It will install the one in the repositories, 2.0.x.x something. If you want 3b5, you need to download it from mozilla.org.

ok, i guess its better check out if i really need the newer versions, but ofc usually newer versions have better and polished things.

Thx

---

### Post by gn2 on 2008-04-19
In light of the fact that you state

> **Ryuki_NdranC said:**
> 1. I'm still a n00b

then always/only install from the repos using Synaptic.

---

### Post by lswest on 2008-04-19
with the backports repo you can install firefox 3, but the package name is different.  Do a ```
apt-cache search firefox 3
``` to find out what the package is called (i think it's just firefox-3.0 but i'm not 100% sure, and it's useful to get into the habit of doing ;))

---

### Post by anjilslaire on 2008-04-19
I'll differ from the crows and suggest going with Hardy later this month since it will have Long Term Support, and will be updated far longer than Gutsy (not being picky, but it is GUTSY, not Gusty. You sound a bit more credible when using the correct name)

This will let you keep updated far longer, more easily from the repo's.

---

### Post by Ryuki_NdranC on 2008-04-19
> **anjilslaire said:**
> I'll differ from the crows and suggest going with Hardy later this month since it will have Long Term Support, and will be updated far longer than Gutsy (not being picky, but it is GUTSY, not Gusty. You sound a bit more credible when using the correct name)

This will let you keep updated far longer, more easily from the repo's.

OMG huge typo :P, thx for correcting me. Yes well so far i'm gonna install Gutsy (:popcorn:) on my laptop to check out some programs and and then install hardy heron when my delivery arrives :) maybe sooner if im done with Gutsy :)

thx for the correction + opinion

---

### Post by bodhi.zazen on 2008-04-19
I think there is always a desire to run the newest, latest, greatest hardware / software.

I think it is a matter of choice or opinion. If you run then newest, latest hardware / software you are more likely to have problems. This is true of any OS, including for example Vista. When Vista came out, and to some extent still today, many things are "broken". Same is true of 8.04.

So how new do you want and how willing are you to put up with "bugs" and bug reports ?

IMO you should not run Alpha or Beta unless you are willing to tolerate bugs and submit bug reports. No developer likes to releasese  an application in Beta to hear it "sucks".

If you want stable, stay in the Ubuntu repos. If there is some feature of some application you need and it is not in the repos either download a .deb or source code from the application home page, most recent stable version. If that does not fix your problem, the go for beta or alpha versions.

Personally I run a stable base and use virtualization or a chroot for testing or "development". If a package seems to work in development environments I add it to my stable environment. Now sometimes you can not test a package in that way (Nvidia beta driver for example) in which case time to mirror your stable base to a testing partition and boot into it.

Just my 2c , HTH.

---

### Post by Ryuki_NdranC on 2008-04-19
> **bodhi.zazen said:**
> I think there is always a desire to run the newest, latest, greatest hardware / software.

I think it is a matter of choice or opinion. If you run then newest, latest hardware / software you are more likely to have problems. This is true of any OS, including for example Vista. When Vista came out, and to some extent still today, many things are "broken". Same is true of 8.04.

So how new do you want and how willing are you to put up with "bugs" and bug reports ?

IMO you should not run Alpha or Beta unless you are willing to tolerate bugs and submit bug reports. No developer likes to releasese  an application in Beta to hear it "sucks".

If you want stable, stay in the Ubuntu repos. If there is some feature of some application you need and it is not in the repos either download a .deb or source code from the application home page, most recent stable version. If that does not fix your problem, the go for beta or alpha versions.

Personally I run a stable base and use virtualization or a chroot for testing or "development". If a package seems to work in development environments I add it to my stable environment. Now sometimes you can not test a package in that way (Nvidia beta driver for example) in which case time to mirror your stable base to a testing partition and boot into it.

Just my 2c , HTH.

Thanks, yes i agree with that, although i didn't understand the part of virtualization, you mean VMWare? I have less than a month in linux, i like the idea and the way linux looks cool AND lets you learn about how things work.

Thx for your opinion :)

---

### Post by bodhi.zazen on 2008-04-19
Yes, VMWare, Virtualbox, or qemu ;)

VMWare server is freely available for linux and in in the Ubuntu repositories, although I download and install directly from VMWare.

There have been a few threads the last few days indicating VMWare may have changed the way they give out serial numbers, but I have not looking into this as I already have one.

---

### Post by Skip Da Shu on 2008-04-19
> **Tatty said:**
> You can find out what is in the backports repo by checking here [http://packages.ubuntu.com/gutsy-backports/]("http://packages.ubuntu.com/gutsy-backports/")

After Ubuntu release, the repos are frozen so the only updates made to them are security patches, or if a serious bug is found which has a simple fix.  If they keep updating the software all the time then it increases the chances of breakages.

The big question, as has already been mentioned, is do you need the latest version?  Most of the time a new version of software offers very little extra compared to the last version.  It is very rare i find that I need a version of software that isnt in the repos.  Its usually much easier to stick to the repos - but its your computer and you have the freedom to set it up however you want, its just down to what suits you best :)

There is a Debian (Ubuntu?) group that updates and supports the BOINC packages.  I get their mailing list just to follow along with the software that my Xubuntu crunchers are dedicated to.

In testing is the v5.10.45 version.  Gutsy still has version v5.10.8.   It's not in backports.

Is there a repository that I can add to my /etc/apt/sources.list so I can install v5.10.45 via synaptic?  I've managed to put it on a couple machines but it's via replacing the executables and I'm told this is not good.

Thanx in advance, Skip


PS: Looking further the packages I'm after appear to be in Hardy (Universe).  Can I add a specific repository to sources.list to install this on my Gutsy system (for knowledge purposes, April 24th is too close to muck about with this now)?

PPS: found answer [HERE]("http://packages.ubuntu.com/hardy/amd64/boinc-client/download")

---


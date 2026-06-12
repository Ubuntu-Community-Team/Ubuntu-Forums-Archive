---
title: "Update Error Message"
date: 2006-06-21
forum: Apple PPC Users
---

### Post by Uta on 2006-06-21
Everytime I use the updater to check my system for updates, I get this message:

"W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-powerpc_Packages)"

How do I correct this, which one should be deleted? Thanks.

---

### Post by BoneKracker on 2006-06-22
I haven't see this before, but here is what I'd do.  (Uta - don't be offended by extra info here that I'm sure you know - it's for newbies that might search this later.)

**First**, I'd clean up any duplicate entries you might have in /etc/apt/sources.list (that could have somehow produced this redundant entry).  For example, by default the file is layed out confusingly with two "dapper" sections (sets of lines that begin with):> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper(If you have added "universe" to the first set, the the second set is redundant and should not be uncommented.)  

If you're not familiar with this file, first go visit your good friend "man".  In addition to other things, there are man pages for most important configuration files.
```
$ man sources.list
```Be patient and make sure you understand it's layout before you go deleting stuff.  Note that there are separate sections for dapper, dapper-updates, dapper-backports, and dapper-security.  You are only looking for dapper (not "dapper-something") lines that mention universe at the end.  There one (and only one) for the binaries (packages).  There should be one (and only one) for source files.

**Second**, replace the offending package list mentioned in the warning (note, the # at the beginning of these lines indicates these commands should be issued as root, which means you should begin them with the word sudo unless you happen to be logged in a root -- which you shouldn't be):
```
# rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-powerpc_Packages
# apt-get update

```(This will delete the file containing the redundant entries and force a fresh re-download of it.)

Let us know if that doesn't work.

---

### Post by Uta on 2006-06-22
Thank you for your very detailed reply! I will post my source.lst because I believe the problem was created when I used Easy Ubuntu to install some mulitmedia plugins. I would very much appreciate advice on which source can be safely removed (commented out).
-----------------------------------------------------------------------------------------------
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free 

# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
--------------------------------------------------------------------------------------------

Thank you.

---

### Post by tidris on 2006-06-22
I don't know much about this, but I think the line that has breezy in it might be part of the problem.

---

### Post by Uta on 2006-06-22
Yes it might have something to do with "breezy"?
I was hoping to get advice on 'exactly which listing' I should comment out from the Again thanks.

---

### Post by tidris on 2006-06-22
[QUOTE=Uta]Yes it might have something to do with "breezy"?
I was hoping to get advice on 'exactly which listing' I should comment out from the Again thanks.[/QUOTE]
This is the line I was refering to

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

In case you didn't know, breezy is the previous version of ubuntu, the current one is dapper.

---

### Post by BoneKracker on 2006-06-24
No, that's not it.  That's a link to a "Penguin Liberation Front" repository.

I don't see an error that would cause the warning message you were getting.  


However, there are a couple of misconfigurations.

Basically you need to make two decisions.  

1.  Choose one:
a) main
b) main and restricted
c) main, restricted and universe
d) main, restricted, universe, and multiverse

2) Choose one:
a) dapper
b) dapper and updates
c) dapper, updates, and security updates
d) dapper, updates, security updates, and backports

When you ran Easy Ubuntu, you seem to have already made the decision to enable universe and multiverse.  So I think you want at least d and c.  You need to decide, but here is a cleaned-up example of what your sources.list file should probably look like.  

Note: making this change is NOT critical and I'm 99% sure it's not going to fix the warning message.  I'm about 40% sure that if you do this AND the rest of what I suggested in my first post, you'll have it covered.  If that doesn't fix it, come back.

```

# /etc/sources.list
# June 23, 2006

## Main dapper release
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## Major bug fix updates to dapper release
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Updates by Ubuntu security team
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe

## Newer versions of some applications which may provide useful features.
## (NOT reviewed or updated by Ubuntu security team).
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

## My custom repositories:
##
## Penguin Liberation Front
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
##
## Opera
deb http://deb.opera.com/opera etch non-free


```

---

### Post by SteveGeorge on 2006-06-24
Hi, 

The original error message is trying to tell you what the problem is. You have duplicate lines for [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) according to it. Looking through the sources list you posted it appears that you've got this twice, referring to 'main' and 'restricted'. 

Consequently, when you run synaptic it tries to get the list of packages for this repository twice; this causes a conflict.

So remove one of the lines and re-update should fix it. I had the same problem after running EasyUbuntu.

---

### Post by Uta on 2006-06-24
Thanks to all that helped (especially BoneKracker) with your instructions, I no longer have an error message. Solved!

---


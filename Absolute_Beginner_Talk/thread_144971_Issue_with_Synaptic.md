---
title: "Issue with Synaptic"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-15
I have been haveing some trouble with Synaptic lately.  Many of the programs I choose to load cannot.  When I hit the reload button, it starts reloading the list, and then I get a message like this:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Is this preventing me from installing programs like Wine. etc.?

---

### Post by Pragmatist on 2006-03-15
Please give us the output of this:
```
cat /etc/apt/sources.list
```

---

### Post by WoodyMahan on 2006-03-15
woody@ubuntu:/usr/share/perl/5.8.7/Net$ sudo cat /etc/apt/sources.list
Password:
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

# PLF
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
## created by arniefreeremoved
woody@ubuntu:/usr/share/perl/5.8.7/Net$

---

### Post by Pragmatist on 2006-03-15
Ok, for testing purposes, backup your /etc/apt/sources.list (I would call it BACKUP_sources.list  some people use sources.list.bak  Use whatever is memorable for you). Then take the copy that is called sources.list (remember you now have a backup) and remove it.  Now open an editor and put this into a file called sources.list:
> 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

I know you have most of these, but you also have a bunch of others, and it is important to do the test with as small a file as possible.  In fact, you probably should try with an even smaller number of repositories and add more until you find the problem.  But, try this for now and let us know what happens.

---

### Post by WoodyMahan on 2006-03-16
OK
I followed the above commands to a T.  I verified that the sources.list in /etc/apt is exactly the same as the code listed.  I DID NOT rebot.  I fired up Synaptic and hit the Reload Button.  I got this:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I guess I need to start removing deb lines (I'll just comment them out if that is OK).  Do you recommend I start with any in particular or just "Start from the Bottom"?

Thanks for the help.

---

### Post by aysiu on 2006-03-16
Try the workaround at the  bottom of this page:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by WoodyMahan on 2006-03-16
OK....That worked.

Now do I have to go back in and reopen my repositories (multiverse, etc)?  Does this affect what I can get through Automatix?

Could this have been caused because I perhaps have an older version of automatix?

Thanks

---

### Post by aysiu on 2006-03-16
I can't imagine an older version of Automatix would give you two conflicting CD-ROM sources and only one online repository.

I don't know what's in a regular Automatix sources.list, though.

---

### Post by WoodyMahan on 2006-03-16
OK.  Thanks for the help.  I'll move along to the next issue (or string of issues).

---


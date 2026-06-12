---
title: "gtkpod - latest version (0.99.10)"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-11-10
Heya! I'm trying to install the latest version of gtkpod (0.99.10) but I keep running into dependency issues. I've tried downloading the deb from [http://www.getdeb.net/release.php?id=1128]("http://www.getdeb.net/release.php?id=1128") but it exits with the error 

```

dpkg: dependency problems prevent configuration of libgpod1:
 libgpod1 depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 libgpod1 depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 libgpod1 depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
dpkg: error processing libgpod1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgpod1

```

which, if I'm reading it right, says a load of my packages are out of date, but i've just done an apt-get update and apt-get upgrade. What can I do? Am I going about this the hard way?

Thanks!!!

---

### Post by ThrobbingBrain66 on 2007-11-10
What version of Ubuntu are you running?  The .deb that you downloaded is compiled against Feisty.  My guess is that you aren't running Feisty....if you are, are you fully up-to-date?

In Feisty, all three of those packages have a version number sufficient to satisfy libgpod's dependencies.

---

### Post by tartarian on 2007-11-10
Nope I'm not running Feisty :( I'm still on Dapper :)
Is that going to be a problem?
Because I really need the upgraded gtkpod :(
Eek!!!
Is there anything I can do (apart from upgrade to feisty!)

---

### Post by ThrobbingBrain66 on 2007-11-10
Upgrade to Gutsy :)

But seriously, that's really your only choice.  Getting .99.10 to work on Dapper would require compiling *at least* 5 different packages.  And I'd be willing to be you'd need to compile the dependencies for those packages as well.

Basically, I'm saying that in this instance, Dapper is living up to it's LTS status.  It's very stable, but the packages are very out of date.

---

### Post by tartarian on 2007-11-10
Haha yeah its an old computer so I try not to push the boundaries, but I need to get my iPod working!!! Excuse my stupidity, but how would I go about upgrading (and which one to?!) Oh and will I loose all my files?
Thankyou so much!!! :)

---

### Post by ThrobbingBrain66 on 2007-11-10
If you take the upgrade method you won't lose your files, however, a clean install is almost always the better choice.  If you have the ability, I would back up all your personal data to an external hard disk / usb drive / whatever you have available.  Then you can download a LiveCD for either Feisty or Gutsy and do a clean install.  

OPTIONAL: *During the install process, you can make a separate /home partition to store all of your settings, configurations and personal data.  This way, you can skip backing up your data if you ever want to do a clean install.*

You could attempt to upgrade, but you'd have to install each version seperately and in order.  So, you'd have to upgrade to Edgy first, then Feisty and then Gutsy (obviously very messy and time-consuming).

---


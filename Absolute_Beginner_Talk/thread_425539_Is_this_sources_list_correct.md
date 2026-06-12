---
title: "Is this sources list correct?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Mairi on 2007-04-27
'Nother dumb question. I'm still having some sort of issue about not getting updates, and was just wondering if it could be my sources list. Here it is.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#AUTOMATIX REPOS START

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
#AUTOMATIX REPOS END

I don't see anything myself, but that means nothing. 
Thanks for any answers.

---

### Post by BarfBag on 2007-04-27
Looks fine to me.  All of the crucial repositories are uncommented.  Maybe your system is already up-to-date?

---

### Post by floke on 2007-04-27
Ditto.
Don't worry about it.

---

### Post by starcraft.man on 2007-04-27
> **Mairi said:**
> 'Nother dumb question. I'm still having some sort of issue about not getting updates, and was just wondering if it could be my sources list. Here it is.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
#AUTOMATIX REPOS END

I don't see anything myself, but that means nothing. 
Thanks for any answers.

Ummm, ya had backports and unsupported repos commented out as well as most of the automatix repos...  That should be better...

Also, go to System > Administration > Software Sources and make sure all of the upper checkboxes on the first and second page are checked. That should be it.

Like the others though, you may just already be up to date...

---

### Post by Mairi on 2007-04-27
Meh, probably. Though it's been up to date for over a week, with no new upgrades and I keep getting a dbus error. I guess I'm fussing for nothing. Thank you kindly. Ubuntu seems happy enough as is. Working like a champ.

---

### Post by Happy_Man on 2007-04-27
That looks fine... if you still have problems, try  [www.ubuntu-nl.org/source-o-matic/](www.ubuntu-nl.org/source-o-matic/)  to make a whole new one.

---

### Post by floke on 2007-04-27
Of course if you *want* updates you could always upgrade to Feisty!

---

### Post by whee on 2007-04-27
Earlier i asked for an original clean feisty sources.list which you get after a clean feisty(final) install.
The comments in it are different from the one from [www.ubuntu-nl.org/source-o-matic/](www.ubuntu-nl.org/source-o-matic/) , but basically they're the same.

Here's that old thread with the original sources.list : [http://ubuntuforums.org/showthread.php?t=425310](http://ubuntuforums.org/showthread.php?t=425310)

---

### Post by Mairi on 2007-04-27
Thank you every one for your quick responses. I'm working on it now, and will see how it goes.  Oh, you have no idea how tempted I am to just hit that update button for Feisty on update-manager. Even if it borked I could just do a clean install of Edgy, with a backup of my home folder. I have Edgy on a 20 Gig Partion, and still have about 16 gig free...I don't store a lot of stuff on my computer. Main thing is always just my settings for things. I'm just not certain, with the trouble people seem to be having. Of course, reading a support forum is not going to give me a true picture of the quality of Feisty, since people come here to get stuff fixed. I do only have 256 RAM, though I've ordered another stick that should be here in a few days. Maybe then.

Thanks again, this is a great forum for a great OS.

---


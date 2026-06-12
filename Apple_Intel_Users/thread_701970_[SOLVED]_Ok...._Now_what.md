---
title: "[SOLVED] Ok.... Now what???"
date: 2008-02-19
forum: Apple Intel Users
---

### Post by KS. on 2008-02-19
Ok, so i'm gathering that the "Synaptic Package Manager" and the "Add/Remove Programs" are a BIG deal of a new install. But I can't seem to use either one. I'm sure SOMEONE else has ran into this, BUT... The errors are:

Synaptic -  

E: Malformed line 74 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


Add/Remove - 


This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


ALSO ... Cyberdork33 said i should use "envy" for the gfx prob. (MBP 2nd Gen.) BUT it says something about "Software index is broken" and gives me this:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

and when i try that it still doesn't work.

Is there a "Step-by-Step" way to go about enabling the right driver and 3D fx on a 2nd Gen. MBP that's made for the "absolute" beginner? 

ANY help on ANY of this would be great. Thanx all for all the support you share with everyone. ;-)

Oh, and i still haven't figured out the wifi thing yet, but i'm just trying to take it one step at a time, i'm plugged in right now, and just trying to figure out the "repository" thing, and the gfx thing.... after that, i'll start on the rest lol. ......*i have a feeling this is going to be a few month process to get this mac running up to par! lol. .... Thanx again everyone.

-KS

---

### Post by aysiu on 2008-02-19
Can you paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
cat /etc/apt/sources.list
```

---

### Post by KS. on 2008-02-19
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/tormodvolden/ubuntu](http://ppa.launchpad.net/tormodvolden/ubuntu) gutsy
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb-src [http://ppa.launchpad.net/tormodvolden/ubuntu](http://ppa.launchpad.net/tormodvolden/ubuntu) gutsy main

---

### Post by cyberdork33 on 2008-02-19
All the problems are related. as the error told that there is a problem with your sources.list file on line 74:
```
http://ppa.launchpad.net/tormodvolden/ubuntu gutsy
``` This is in an incorrect format, and I do not know what this ppa is for, so wherever you got it, you need to double check it and correct it. I think it just needs a 'main' at the end:
```
http://ppa.launchpad.net/tormodvolden/ubuntu gutsy main
```
Otherwise just comment out that line by putting a '#' in the front. Then you should be able to fix the cache:
```
sudo apt-get update
```

Envy is still probably the easiest way for you to install the best ATI drivers, but that is not going to work until you fix the package manager.

---

### Post by aysiu on 2008-02-19
> **KS. said:**
> ```
**deb http://ppa.launchpad.net/tormodvolden/ubuntu gutsy**
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports restricted main universe multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security restricted main universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb-src http://ppa.launchpad.net/tormodvolden/ubuntu gutsy main
``` This (the bolded line) is the malformed line in the sources.list file in the /etc/apt directory. Do you see how it differs from the other ones?

---

### Post by KS. on 2008-02-19
i feel like such a jackass.... i hate to keep bothering everynoe with stuff that i SHOULD know, OR learn! but i do thank you all for the help and support.

Now, what i don't get is: 

Put a "#" in front of  what? the sudo apt-get update? ...or something else?


Thanx again.

-KS

---

### Post by aysiu on 2008-02-19
This link will explain how to edit system files (of which /etc/apt/sources.list is one):
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Putting a # at the beginning of a line in a configuration file tells the system "Ignore the rest of this line."

---

### Post by ayenack on 2008-02-19
You need to comment "#" out that entry in /etc/apt/sources.list like this.

# deb [http://ppa.launchpad.net/tormodvolden/ubuntu](http://ppa.launchpad.net/tormodvolden/ubuntu) gutsy

EDIT:
Do this in terminal.

**gksu gedit /etc/apt/sources.list** (To open the sources.list file and comment it out as shown above.)

Then.

**sudo apt-get update** (To update your sources.list)

BTW aysiu IceBuntu seems to be coming along nicely. I put a how to up on the IceBuntu forums on installing IceBuntu to a pendrive or any media really. I installed it to a 1GIG USB pendrive. I like it alot.

---

### Post by KS. on 2008-02-19
ok, found the prob, (in 3rd party soft.) ... fixed that... now have access to my "add/remove" AND synaptic!!!! *OH HAPPY DAY!!!* lol.... OH! hold on... going try the envy thing! ........OK that "seemed" to work, i THINK i'll have to reboot to find out. ..... wish me luck!


THNX EVERY1!!

-KS

---

### Post by ayenack on 2008-02-19
Quick suggestion. Before installing any graphics driver do this.

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup** ("cp" stands for copy. This will copy your xorg.conf and rename it xorg.conf_backup leaving the original in place)

Then if you end up at the command line you can restore your xorg.conf & GUI like this.

**sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf** (This will just copy the backup and restore the xorg.conf file to it's original settings.)

Be sure to use capitol "X" in all instances of "X11".

---


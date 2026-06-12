---
title: "[SOLVED] my add remove programs gui"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by 2manydrugsago on 2008-01-21
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
  

Umm what?

How do I follow these instructions?

---

### Post by emarkd on 2008-01-21
Not sure what you're trying to do, but here goes:

1.  Open Synaptic by clicking on System - Administration - Synaptic Package Manager
2.  Check for broken packages by clicking on the Edit menu and selecting "Fix Broken Packages"
3.  Reload the repositories by clicking the Reload button

Does this help?

---

### Post by 2manydrugsago on 2008-01-21
oh no i get this when I open synaptic 

E: Type '“deb' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

hari cari is looking quite appealing.

---

### Post by emarkd on 2008-01-21
Sounds like there's an error in your sources file.  Can you run this from a command line and paste the output here:

```
cat /etc/apt/sources.list
```

---

### Post by 2manydrugsago on 2008-01-21
evan@evan-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
“deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”
evan@evan-desktop:~$

---

### Post by emarkd on 2008-01-21
I think apt doesn't know what to do with those quotes on the last line of the file.  From the commandline, run
```

sudo gedit /etc/apt/sources.list
```

When the editor opens, remove those quotes from both ends of the last line and save it.  Then try whatever you're doing again

BTW:  That repository on the last line is for Feisty.  If you're running Gutsy you really shouldn't use it.  I think you want to replace that entire line with:

deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main

---

### Post by frup on 2008-01-21
I think it's this “deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

type 

gksudo gedit /etc/apt/sources.list

in terminal and remove at least the " " on each side. Save and then type sudo apt-get update and try what ever you wanted to do again.

---

### Post by 2manydrugsago on 2008-01-21
ohh its fixededed like umm uhh somthing fixed i guess. anyway thanks a million. I was trying to get a  super nintendo  emulator to work, any ideas?

---

### Post by bodhi.zazen on 2008-01-21
And you should NOT mix Feisty repos with Gutsy Unless you KNOW what you are doing.

---

### Post by 2manydrugsago on 2008-01-21
great signature! and I can tell you without a doubt I HAVE NO IDEA what im doing.

---

### Post by 2manydrugsago on 2008-01-21
do I need to post elsewhere about the emulator?

---

### Post by bodhi.zazen on 2008-01-21
If you would mark this thread as solved that would be great.

And I suggest you start a new thread, I do not think you are going to get advice on your emulator in a thread titled "my add remove programs gui" ;)

---

### Post by 2manydrugsago on 2008-01-22
How do I mark it as solved? In the title? on my badger?

---

### Post by emarkd on 2008-01-22
I've never used it, but UbuntuGuide recommends ZSNES.  See [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Super_Nintendo_Emulator_.28ZSNES.29_1.510_for_i386.2FAMD64](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Super_Nintendo_Emulator_.28ZSNES.29_1.510_for_i386.2FAMD64) for more info.

---

### Post by bodhi.zazen on 2008-01-22
> **2manydrugsago said:**
> great signature! and I can tell you without a doubt I HAVE NO IDEA what im doing.

On you very first post, where you started this thread, go under thread tools -> mark as solved

---


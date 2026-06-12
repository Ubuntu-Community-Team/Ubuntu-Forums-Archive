---
title: "Pidgin 2.4.1"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-04-08
I removed Version 2.2.1 and tried to install the pidgin data and the libpurple from get deb.net so I could get the 2.4.1

Problem:  Even though its installed when I click on the download for any of them, I cant get the standard "gdebi Package installer" to pop up directing it like "here i am!:lolflag:".  What in the world am i missing or could try to get it to regonize gdebi so I can get the 2.4.1?

---

### Post by sports fan Matt on 2008-04-08
this sounds like an easy fix so im trying to figure out why i cant figure it out...:lolflag:

---

### Post by z0mbie on 2008-04-08
Put then in one folder & In commandline just type in ```
sudo dpkg -i *.deb
```

---

### Post by sports fan Matt on 2008-04-08
That didnt work..I was able to install using sudo apt-get install pidgin 2.2 but id like to install 2.4.1..Here is the error: dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

---

### Post by sports fan Matt on 2008-04-08
I think i borked my sources list but im not sure what i need to add..any advice?

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe #Added by software-properties
## Avant Window Navigator

deb [http://people.linux.org.tw/~pcman/ubuntu](http://people.linux.org.tw/~pcman/ubuntu) ./
deb [http://ppa.launchpad.net/ubuntu-backporters/ubuntu](http://ppa.launchpad.net/ubuntu-backporters/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/ubuntu-backporters/ubuntu](http://ppa.launchpad.net/ubuntu-backporters/ubuntu) gutsy main

---

### Post by dummyhead3 on 2008-04-08
Can't believe ppls use Pidgin.. especially if it's for M,S and N... if it is you should tru emesene. it's much better than Pidgin.

---

### Post by dummyhead3 on 2008-04-08
You're supposed to enter the name of the file and the path (/home/yourmemr/.../watever.deb) instead of * . You can simply try double-cliking on the file.

---

### Post by neurostu on 2008-04-08
So what error do you get when you run
```

sudo dpkg -i pidgin2.4 package.deb

```

---

### Post by sports fan Matt on 2008-04-08
dpkg: error processing pidgin2.4 (--install):
 cannot access archive: No such file or directory
dpkg: error processing package.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pidgin2.4
 package.deb

---

### Post by neurostu on 2008-04-08
That error looks like the .deb file might be corrupted. Try downloading it again.

---

### Post by sports fan Matt on 2008-04-08
ok,i'll give it a shot..:)

---

### Post by sports fan Matt on 2008-04-08
ok..The download refused to move when i chose "save file" and the only option im presented with firefox -3.0b5..How could I change that to open with or save file "gdebi"?  Its installed through symnaptic it i guess cant find symnaptic..

---

### Post by sports fan Matt on 2008-04-08
one thing i do see, if it helps is in my bottom of my firefox it says one active download a few seconds remaining but there are zero there and they wouldnt run anyway..Could i have sources from my sources list missing that I need to install DEB. files?

---

### Post by sports fan Matt on 2008-04-08
this error pops up now: cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by sports fan Matt on 2008-04-09
All fixed ..i redownloaded all the deb's..now if i could only remove awesome window manager im all set :)

---

### Post by neurostu on 2008-04-09
sox fan Matt, the real question I have to ask is:
red sox or white sox?

---

### Post by sports fan Matt on 2008-04-09
Actually Both..I live about 15 minutes from the cell, and cant stand the yankees nation, so Go both teams, although i've never been to boston

---

### Post by xelapond on 2008-04-09
Nevermind, didn't realize there was a second page and it was all good:)

---

### Post by neurostu on 2008-04-09
Boston is a great city! If you ever get a chance to go to fenway you should totally jump on it. Fenway is an amazing park with a atmosphere that is getting lost more and more in professional "corporate" sports (*cough Yankees *cough).

---

### Post by sports fan Matt on 2008-04-09
15 days to Christmas!  I will probably wait and do a dist upgrade in a week after its released

Yeah, Wrigley is the same way

---

### Post by rudihawk on 2008-04-16
> **dummyhead3 said:**
> Can't believe ppls use Pidgin.. especially if it's for M,S and N... if it is you should tru emesene. it's much better than Pidgin.

It looks like pidgin, MSN works fine on Pidgin and Pigin also lets me use gtalk and IRC, all from one application. That beats having one application for each protocol that I would like to use. :)

---


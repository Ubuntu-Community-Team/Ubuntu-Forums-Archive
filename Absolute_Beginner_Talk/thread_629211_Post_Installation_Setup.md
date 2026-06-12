---
title: "Post Installation Setup"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by yeehi on 2007-12-02
Could somebody link me to a good page showing the good things to do right after installation/

Thank you!

---

### Post by shuttleworthwannabe on 2007-12-02
have you tried ubuntuguide.org? or even [this]("http://articles.slicehost.com/2007/11/6/ubuntu-gutsy-setup-page-2") site?

---

### Post by Daveth on 2007-12-02
or this long rambling post......

[http://ubuntuforums.org/showthread.php?t=584125](http://ubuntuforums.org/showthread.php?t=584125)

---

### Post by yeehi on 2007-12-02
I wonder whtere the instructions [here]("http://www.cs.cornell.edu/w8/~djm/ubuntu/gutsy/#add-repositories") are still valid for gutsy gibbon.

For example,

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

Does the text above still need to be added? And what if you are not in the usa? Should all the **us.archive** be changed to, eg, **uk.archive**?

---

### Post by Partyboi2 on 2007-12-02
> **yeehi said:**
> I wonder whtere the instructions [here]("http://www.cs.cornell.edu/w8/%7Edjm/ubuntu/gutsy/#add-repositories") are still valid for gutsy gibbon.

For example,



Does the text above still need to be added? And what if you are not in the usa? Should all the **us.archive** be changed to, eg, **uk.archive**?

If you like you can just go to Menu>System>Admin>Software Sources and add them by clicking on a box, Or you can add them like your example says by in a terminal:
```
gksudo gedit /etc/apt/sources.list
```At the bottom of the list add those examples, save and then in a terminal
```
sudo apt-get update
```You dont have to add them, but personally I find having them added makes life easier 
Under "Software Sources you can also change the server where you get your updates from eg the uk.

---

### Post by yeehi on 2007-12-02
Thank you!

But do i have to manually change the us to uk if i paste those links into the terminal?

Also, I got the following error message after running apt- get update

> Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems


---

### Post by Partyboi2 on 2007-12-02
>                               Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com]("http://archive.canonical.com/") gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_d  ists_gutsy_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dis  ts_gutsy-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") gutsy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dis ts_gutsy-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dis ts_gutsy-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") gutsy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dis ts_gutsy-security_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problemsYou will get this when you already have this added to your source.list. Source.list does not like to have duplicate entries. Easy way to fix it is to do as it says in a terminal run:
```
sudo apt-get update
``` you may have to run it a second time, but it should clean it up.

>  But do i have to manually change the us to uk if i paste those links into the terminal?You can leave then as they are, all it means is that its going to look at the us server instead of the uk server to get updates. You can try changing the us to uk, I have never had to change it. The easiest way to change the server and adding to source.list is by Menu>System>Admin>Software Sources. Other wise you might end up with duplicate entries. What you are trying to add from that website might be already added to source.list check that there is only one entry not a double up.

P.S I find that having the server set to the main one works better, when I have used the australian server I get problems like timeouts. So in my experience I find that the main server works best.
:)

---

### Post by ruibernardo on 2007-12-02
> **yeehi said:**
> Could somebody link me to a good page showing the good things to do right after installation/

Thank you!

Install and enable multimedia: [Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413625")

Install firestarter (firewall, needed if your going to enable any server or share files through the network or Internet): [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

Install sbackup for backup: [http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

---

### Post by yeehi on 2007-12-03
Thank you for this help.

I tried to fix the list as you suggested. It went OK, but at the end left me with this error message:
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now new updates are available, but i can't install them, as this message appears when i try.

---

### Post by Partyboi2 on 2007-12-03
In a terminal try:
```
dpkg --configure -a
```

---

### Post by yeehi on 2007-12-03
> requested operation requires superuser privilege

I do su 
type in my password, but it says that isn't the password. It works for when i do apt, though. I tried the password several times...

I went to manage users, changed the password of root, and tried to do su again, but it still wont work!?

---

### Post by Partyboi2 on 2007-12-03
Sorry its almost past my bed time, its meant to have sudo before
 
```
sudo dpkg --configure -a
```

---

### Post by yeehi on 2007-12-03
That worked!

Now, if you still are awake 1 minute longer -- when i now try to do the update package it tells me I have a broken package and to trace it, and this error:

You are so helpful!

> W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_multiverse_binary-amd64_Packages)

---

### Post by Partyboi2 on 2007-12-03
Can you post your source.list
```
cat /etc/apt/sources.list
```
Also can you post the details about the broken package please

---

### Post by yeehi on 2007-12-03
> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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

##I added the bonkers below
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse


I can't repeat the broken package message or work out how to trace a broken package.

---

### Post by Partyboi2 on 2007-12-03
Open up sources.list
```
gksudo gedit /etc/apt/sources.list
```delete the ones in red then:
```
sudo apt-get update
``````
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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

##I added the bonkers below
[COLOR=Red]  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse[/COLOR]  gutsy-updates main restricted universe multiverse  gutsy-backports main restricted universe multiverse    
```

---


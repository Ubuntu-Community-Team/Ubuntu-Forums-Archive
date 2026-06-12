---
title: "how to disable additional repositories??"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by thespankguy on 2007-10-20
i found this link:

[http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)

and decided to go ahead and go through what it said even though i'm running 7.1 and not 7.04. i figured if it said to do something that 7.1 already had or had something better that it just wouldn't work or wouldn't matter in the long run. 

i've been trying to install things like adobe reader, some video players  (like what were on that link)  and some apt get commands and it keeps giving me this error everytime. 

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

can i undo what i did in the first step when i enabled additional repositories? (i don't even know what they are)

---

### Post by Pumalite on 2007-10-20
Backup first:
sudo cp /etc/apt/souces.list /etc/apt/sources.list.back, then:
gksudo gedit /etc/apt/souces.list
Comment out (#) the offending line, save, exit, and reboot

---

### Post by NilsE on 2007-10-20
Not knowing how good bad or indifferent your sources.list is just delete everything in it then copy the following into it.  This by the way is a default copy without sources. You can add sources back or add more repositories in the system/Administration/Software Sources utility

In a terminal do: gksudo gedit /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
```

---

### Post by shae on 2007-10-20
This is easily fixed.

Run the following commands:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list 
```
This removes the repository.
Be extremely careful when typing that line.  Copy and paste might be a better option.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
This adds the correct medibuntu repository for gutsy (7.10).
Then you should try:
```
sudo apt-get update
```

If you still get errors, please post them again.

---

### Post by thespankguy on 2007-10-20
i followed what shae posted and it works fine now. thanks a lot.  i'll experiment more with installing stuff later. i'm leaving for the ohio state game

---

### Post by shae on 2007-10-20
> **thespankguy said:**
> i followed what shae posted and it works fine now. thanks a lot.  i'll experiment more with installing stuff later. i'm leaving for the ohio state game

Great to hear!

---

### Post by Paqman on 2007-10-20
> **thespankguy said:**
> (i don't even know what they are)

A repository is just an online software library. Once you've added the address of it into your sources.list (or the Software Sources GUI) you can then download and install all the packages through apt-get/Synaptic.

---

### Post by Darganot on 2007-10-20
Only thing missing from this thread is the gpg key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
```

This can be done even after adding the repos and trying to update.  Of course the needed packages:

```

sudo apt-get install w32codecs
sudo apt-get install libdvdcss2
```

:popcorn:

---

### Post by thespankguy on 2007-10-20
you guys are awesome, thanks a lot

---

### Post by Dr Small on 2007-10-20
Please remember to mark your thread as [SOLVED] from Thread Tools ;)

---


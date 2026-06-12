---
title: "[SOLVED] I messed something up and can't fix"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-29
I was trying to figure out how to install KDE on Gnome and I messed with the source list and now I get this when I try to open Add/Remove:

 This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I tried the given commands but they didn't work. :confused:

---

### Post by LaRoza on 2007-11-29
To install kde, run:

```

sudo aptitude install kde-core

```

---

### Post by LaRoza on 2007-11-29
> **449 said:**
> This is a major failure of your software management system.

Was that the error?

---

### Post by 449 on 2007-11-29
> E: Type 'See' is not known on line 2 in source list /etc/apt/sources.list
E: Type 'See' is not known on line 2 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'See' is not known on line 2 in source list /etc/apt/sources.list
E: The list of sources could not be read.


This is what I got in terminal.

---

### Post by shae on 2007-11-29
Post the results of:
```
sudo apt-get update
sudo apt-get -f install
cat /etc/apt/sources.list
```

---

### Post by LaRoza on 2007-11-29
It looks like the file had a line in it that was uncommented (See looks like a human sentence.)

Open the file and comment out line two if it is a sentence.

---

### Post by PmDematagoda on 2007-11-29
> **LaRoza said:**
> To install kde, run:

```

sudo aptitude install kde-core

```

Isn't the command used to install KDE on Ubuntu
```

sudo aptitude install kubuntu-desktop
```

LaRoza?

---

### Post by 449 on 2007-11-29
> erik@erik-desktop:~$ sudo apt-get update
E: Type 'See' is not known on line 2 in source list /etc/apt/sources.list
erik@erik-desktop:~$ sudo apt-get -f install
E: Type 'See' is not known on line 2 in source list /etc/apt/sources.list
E: The list of sources could not be read.
erik@erik-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
 See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
 newer versions of the distribution.

 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
 Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
 Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

 Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
 Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
 Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
 Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
 Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
 Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
erik@erik-desktop:~$ 

 

:confused:

---

### Post by Scunizi on 2007-11-29
Here's a copy of my sources.list file.  It's clean and has universe and multiverse added.  Make sure your's is the same.  Then 'sudo apt-get update',  'sudo apt-get upgrade' then for kde you can do sudo apt-get install kde-core' or my method.. 'sudo apt-get install kubuntu-desktop'.  To use kde instead of gnome, on the log-in screen change 'sessions' to kde and continue log-in like normal.

> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed main universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main universe

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

---

### Post by PmDematagoda on 2007-11-29
Open up the sources.list file for editing using:-
```

sudo gedit /etc/apt/sources.list
```

And uncomment these lines:-

```
Line commented out by installer because it failed to verify:

See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
newer versions of the distribution.
```

to make them look like this:-

```
#Line commented out by installer because it failed to verify:

#See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
#newer versions of the distribution.
```

Save the file, do:-
```

sudo apt-get update
``` 

And try installing KDE again.

---

### Post by 449 on 2007-11-29
Thanks Scunizi. :)

Now if I may ask one more thing. The main reason for wanting Kubuntu is for Ktorrent, is there a way to install Ktorrent in Gnome?

---

### Post by PmDematagoda on 2007-11-29
Sure, install Ktorrent using:-

```
sudo apt-get install ktorrent
```

---

### Post by LaRoza on 2007-11-29
> **PmDematagoda said:**
> Isn't the command used to install KDE on Ubuntu
```

sudo aptitude install kubuntu-desktop
```

LaRoza?

No, although that command does install KDE, it installs everything that Kubuntu has. kde-core gives you much less, just KDE and a few other apps.

---

### Post by 449 on 2007-11-29
Thanks!

Oh, and ONE more thing I promise. :popcorn:

What's the command to install Flash, the one I tried didn't work.

---

### Post by LaRoza on 2007-11-29
> **449 said:**
> 
What's the command to install Flash, the one I tried didn't work.

What did you try?

```

sudo aptitude install flashplugin-nonfree

```

Make sure the repository is enabled.

---

### Post by PmDematagoda on 2007-11-29
> No, although that command does install KDE, it installs everything that Kubuntu has. kde-core gives you much less, just KDE and a few other apps.

That makes sense, thanks for that LaRoza:).

---

### Post by LaRoza on 2007-11-29
> **PmDematagoda said:**
> That makes sense, thanks for that LaRoza:).

No problem.

---


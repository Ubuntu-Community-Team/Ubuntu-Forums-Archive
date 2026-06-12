---
title: "Nothing at all is downloading correctly"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Zieb on 2007-04-21
Okay, back when I had Ubuntu Brezzy Badgar before I had no trouble using synaptic or the xterme to get whatever I needed on the computer.  However, sinc reinstalling it, nothing at all has worked.  I tried to add AMSN and a couple media players at no luck.  So I thought maybe I needed to get at least 6.06 as it's still supported, so I did.  It took three tries, but finally the upgrade worked.  However, I still can't get anything to download.  Everytime it says some libraies are missing or didn't install correctly or something else.  I get the same thing when I try using the xterm. 

Anyone know what might be wrong?

---

### Post by taurus on 2007-04-21
Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by Zieb on 2007-04-21
No idea what any of it means, but this is what I got.  

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe



I just finally got aMSN to install, so I don't know.  That's the first thing to work in two days, and that was only on my third or fourth try.  With my luck, it just decided to fix itself because I asked for help.  That's what computers always do to me.

---

### Post by taurus on 2007-04-21
No wonder you have all kind of problems.  You are **not** supposed to mix breezy with dapper repos in your /etc/apt/sources.list.  If you are running dapper right now, you need to replace **breezy** with **dapper** or vice versa in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Then, update and upgrade it.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Zieb on 2007-04-21
What do you mean by "replace breezy with dapper"?  Can I do that through Synaptic?

---

### Post by Happy_Man on 2007-04-21
No, he means actually go through /etc/fstab and change all them words -- either to Breezy or Dapper, whichever you're running.

---

### Post by Zieb on 2007-04-21
That's what I was afraid of. :(

So where ever it says breezy, I should change it to read "dapper"?

I'm running 6.06, which, to my understanding, is Dapper, right?

---

### Post by eyelessfade on 2007-04-21
> **Zieb said:**
> What do you mean by "replace breezy with dapper"?  Can I do that through Synaptic?

Yes in Settings --> Reprositories

---

### Post by Zieb on 2007-04-21
> **eyelessfade said:**
> Yes in Settings --> Reprositories

So just uncheck the "breezy" repositories then?

---

### Post by taurus on 2007-04-21
Type this command from a terminal.

Applications -> Accessories -> Terminak
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by eyelessfade on 2007-04-21
> **Zieb said:**
> So just uncheck the "breezy" repositories then?

Or change them to dapper

---


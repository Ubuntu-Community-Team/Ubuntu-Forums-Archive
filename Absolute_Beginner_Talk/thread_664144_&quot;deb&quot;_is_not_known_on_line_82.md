---
title: "&quot;deb&quot; is not known on line 82"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by domeboy on 2008-01-10
Trying to install Automatix2 and I keep getting this...


E: Type '“deb' is not known on line 82 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by wolfen69 on 2008-01-10
post the output of:
 cat /etc/apt/sources.list

---

### Post by domeboy on 2008-01-11
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

---

### Post by Cypher on 2008-01-11
Modify the file and remove the quotes around the last line in the file.
```

sudo gedit /etc/apt/sources.list

```

---

### Post by macogw on 2008-01-11
Also, don't use Automatix.  [Automatix is Actively Dangerous to Systems](http://mjg59.livejournal.com/77440.html), according to an Ubuntu developer.   If you need codecs, they're all in the ubuntu-restricted-extras package in Add/Remove.  Java is sun-java6-jre.  For DVDs, just google for libdvdcss2.

---

### Post by erfahren on 2008-01-11
agreed - tell us the programs you need and we'll help you out- Automatix is no longer needed

EDIT: what version of Ubuntu? - we can help you set up your sources.list to enable all the repos

---

### Post by macogw on 2008-01-11
Delete all those lines that say "failed to verify" or have a # at the beginning (they're commented out, so they're not doing anything..this'll just make it cleaner)....it just means you weren't online when you installed, so it freaked.

---

### Post by bodhi.zazen on 2008-01-11
> **wolfen69 said:**
> post the output of:
 cat /etc/apt/sources.list

Or , if you know the line, lets see it :

```
cat -n /etc/apt/sources.list | grep 82
```

---

### Post by overdrank on 2008-01-11
And please correct me if I am wrong but why have a edgy repo? A little outdated.

---

### Post by domeboy on 2008-01-13
Thank for the info on Automatix....
When I try to use the update manager i get this:

"Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 82 in source list /etc/apt/sources.list, E:The list of sources could not be read.'"

I get the same message when I 'sudo apt-get install gedit'.
If I can't use gedit there, is there an alternative?
Does it matter if I'm running Xubuntu?

Thanks for all the help!

---

### Post by timbounceback on 2008-01-13
remove the quotation marks on the last line of your sources.list, then open up a terminal and run:
sudo apt-get update

---

### Post by Rui Pais on 2008-01-13
> **domeboy said:**
> ...
If I can't use gedit there, is there an alternative?
Does it matter if I'm running Xubuntu?

Thanks for all the help!

If you are using Xubuntu you must use mousepad instead of gedit:
```
sudo gedit /etc/apt/sources.list
```


hth

---

### Post by domeboy on 2008-01-13
I figured out that i needed to use mousepad instead of gedit

thank you for help and patience!



(consider this solved)

---

### Post by erfahren on 2008-01-13
glad you got it worked out

you *can* install gedit and use it for your text editor - (I did when I started using Xubuntu) - it has more features than mousepad (and doesn't take as long to type into the terminal !)

also, (I guess I should have mentioned this before) - you can add the Medibuntu repository as well - it has some packages that aren't available in the Ubuntu repos (realplayer, acroread, googleearth, some codecs, etc.)

this shows how to add the repo and the key (it works for Xubuntu): [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

--- just wanted to mention that

you can mark this thread as "Solved" by going to the "Thread tools" above the first post

good luck!

---


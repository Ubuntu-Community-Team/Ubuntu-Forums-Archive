---
title: "[SOLVED] ADD/REMOVE not working"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Hutom on 2007-03-31
I was trying to install mplayer, which I didn't find in package manager in spite of having all repositories enabled. I tried to re enable it through the software sources tab.   Following error occurred --

"[COLOR="Red"]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preference.[/COLOR] "

I tried to check my source list. Typed "[COLOR="Red"]cat /etc/apt/sources.list[/COLOR]" in the terminal. Following reply came --

> #
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
#AUTOMATIX REPOS END

I tried to remove AUTOMATIX. Now my add/remove is not working. It says,

[COLOR="Red"]This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.[/COLOR]

So, what should I do now?

---

### Post by useResa on 2007-03-31
Could you try the command as proposed?
You can do this by opening a terminal (Applications --> Accessories --> Terminal) and enter the command ```
sudo apt-get update
```

Next could you post the result of this command?

---

### Post by Hutom on 2007-03-31
Problem resolved. Anyway thanks to useResa.O:)

---

### Post by Maestro23 on 2007-03-31
> **Hutom said:**
> Problem resolved. Anyway thanks to useResa.O:)

Good deal.  Could you go back and edit your first post to RESOLVED.  Under advanced.
Thanks.

---

### Post by Hutom on 2007-03-31
Now add/remove and repository download and everything else is working fine. But I still cannot open a vcd. Totem - xine, vlc player, mplayer --- nothing is working.

---


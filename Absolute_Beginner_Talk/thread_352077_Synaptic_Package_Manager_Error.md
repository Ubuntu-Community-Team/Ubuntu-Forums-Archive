---
title: "Synaptic Package Manager Error"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by JBen on 2007-02-02
When I try to update my system, I get this error:
E: Type 'linux-restricted-modules-<kernel>-generic' is not known on line 32 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


What do I change in the repository menu?

---

### Post by meng on 2007-02-02
Did you add something to the repository list? If so, go to Settings > Repositories and delete the repository that looks like the offending line of the error message. Otherwise, drop to the command line and show us what the computer's response is to this command:
cat /etc/apt/sources.list

---

### Post by JBen on 2007-02-02
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
linux-restricted-modules-<kernel>-generic

---

### Post by meng on 2007-02-02
sudo nano -B /etc/apt/sources.list

and delete that final line. What the heck is that doing there?

then ctrl-x to close (and save).

---

### Post by JBen on 2007-02-02
Thank you! Well, I'm in the process of trying to determine if my video card will support 3d games, and so I tried to download the file through synaptic that I thought my video card needed. Turns out I already had that file anyway. I still can't get the game to run, but I got a completely different game to run, so I think it maybe be the original game that just doesn't like me.

---


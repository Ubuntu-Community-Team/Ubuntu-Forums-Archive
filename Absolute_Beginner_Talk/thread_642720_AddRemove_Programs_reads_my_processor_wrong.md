---
title: "Add/Remove Programs reads my processor wrong"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by fester225 on 2007-12-16
I want to install VMWare. When I try to download it in ADD/REMOVE PROGRAMS I'm told i386 processors aren't supported by the program. KDE says I have an i686. How do I convince ADD/REMOVE PROGRAMS to install VMWare?

---

### Post by PmDematagoda on 2007-12-16
Please post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by fester225 on 2007-12-17
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by mgmiller on 2007-12-17
Are you sure you are running the right kernel?  If you are running the i386 kernel, this may be your problem.  Post the output of:

```
uname -a
```

You should be running the generic kernel which supports SMP and etc.

I have an AMD 64 3200+  this is the output of the above command for me:
```
marty@tux:~$ uname -a
Linux tux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
marty@tux:~$ 
```

---

### Post by fester225 on 2007-12-17
dan@dan-linux:~$ uname -a
Linux dan-linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by mgmiller on 2007-12-18
OK, you seem to have the right kernel.  
Did you try installing through synaptic package manager instead of add/remove programs.  
They should both be front ends to apt and hence should give the same info, but sometimes I have found they don't.

---

### Post by fester225 on 2007-12-18
Synaptic didn't have VMWare listed.

---

### Post by mgmiller on 2007-12-19
Apparently a kernel virtual machine is built into Ubuntu since 7.04.  Here is some documentation for it:

[https://help.ubuntu.com/community/KVM]("https://help.ubuntu.com/community/KVM")

---


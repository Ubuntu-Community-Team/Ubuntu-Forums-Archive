---
title: "MPlayer install problem"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2006-08-19
Having a problem instaling the MPlayer.... iv done everything it says in the README file but i still get this error...

u5@u5tabil:/usr/local/MPlayer-1.0pre8$ sudo ./configure Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... not found
Checking for gcc version ... not found
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... not found
Checking for gcc-3.2 version ... not found
Checking for gcc-3.1 version ... not found
Checking for gcc3 version ... not found
Checking for gcc-3.0 version ... not found
Checking for cc version ... not found

*** Please downgrade/upgrade C compiler to version gcc-2.95.x or gcc-3.x! ***

You are not using a supported compiler. We do not have the time to make sure
everything works with compilers other than the ones we use.  Use either the
same compiler as we do, or use --disable-gcc-checking but DO *NOT* REPORT BUGS
unless you can reproduce them after recompiling with a 2.95.x or 3.x version!

Note for gcc 2.96 users: Some versions of this compiler are known to miscompile
mplayer and lame (which is used for mencoder).  If you get compile errors,
first upgrade to the latest 2.96 release (minimum 2.96-85) and try again.
If the problem still exists, try with gcc 3.x (or 2.95.x) *BEFORE* reporting
bugs!

        GCC 2.96 IS NOT AND WILL NOT BE SUPPORTED BY US !

    *** For details please read DOCS/HTML/en/users-vs-dev.html ***


Error: Bad gcc version

Check "configure.log" if you do not understand why it faild

Anyone know what to do? ](*,)

---

### Post by taurus on 2006-08-19
Open a terminal and install build-essential as

```
sudo aptitude install build-essential
```
Otherwise, install mplayer from the repos...

---

### Post by U5tabil on 2006-08-20
> **taurus said:**
> Open a terminal and install build-essential as

```
sudo aptitude install build-essential
```
Otherwise, install mplayer from the repos...

when i type that i get this 

u5@u5tabil:/$ sudo apitude install build-essential
sudo: apitude: command not found

](*,)

---

### Post by noof on 2006-08-20
```
sudo apt-get install build-essential
```

---


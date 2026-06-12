---
title: "deb package isn't located by apt-get install"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by tlinux on 2007-05-20
I downloaded the "build-essential" deb package, moved it to Kubuntu which isn't connected to the Internet yet, and tried to install it. It didn't work. Here's what happened:

tom@emachine:~$ cd /home/tom/debPackages
tom@emachine:~/debPackages$ [COLOR=Red]ls -l[/COLOR]
total 5533
-r-xr-xr-x 1 tom tom 2512860 2007-05-19 22:33 binutils_2.17cvs20070426-6_i386.deb
[COLOR=Red]-rwxr-xr-x 1 tom tom    6982 2007-05-20 07:24 build-essential_11.3_i386.deb[/COLOR]
-r-xr-xr-x 1 tom tom 3136984 2007-05-19 22:35 coreutils_5.97-5.3_i386.deb
tom@emachine:~/debPackages$ [COLOR=Red]sudo apt-get install build-essential[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
[COLOR=Red]E: Couldn't find package build-essential[/COLOR]
tom@emachine:~/debPackages$


The install instruction is executed while in the debPackages directory where "build-essential" is located. Why can't it find the package? What do I need to do to get "apt-get install" to recognize it?

Thank you.

---

### Post by Bachstelze on 2007-05-20
apt-get doesn't work for locally downloaded package. They're installed at a lower level, with dpkg -i. But why did you download build-essential ? It's on your Ubuntu CD...

---

### Post by tlinux on 2007-05-20
I didn't get build-essential from the CD because I didn't know it was there. Once you told me I looked and found it. However, it was in some obscure folder that I would never have opened had you not told me.

I tried dpkg and here's what I got:


tom@emachine:~$ cd /home/tom/debPackages
tom@emachine:~/debPackages$ ls -l
total 5533
-r-xr-xr-x 1 tom tom 2512860 2007-05-19 22:33 binutils_2.17cvs20070426-6_i386.deb
-rwxr-xr-x 1 tom tom    6982 2007-05-20 07:24 build-essential_11.3_i386.deb
-r-xr-xr-x 1 tom tom 3136984 2007-05-19 22:35 coreutils_5.97-5.3_i386.deb
tom@emachine:~/debPackages$[COLOR="Red"]sudo dpkg -i build-essential
Password:[/COLOR]
dpkg: error processing build-essential (--install):
 cannot access archive: No such file or directory
[COLOR="Red"]Errors were encountered while processing:
 build-essential[/COLOR]
tom@emachine:~/debPackages$ [COLOR="Red"]sudo dpkg -i build-essential_11.3_i386.deb[/COLOR]
(Reading database ... 75271 files and directories currently installed.)
Preparing to replace build-essential 11.3 (using build-essential_11.3_i386.deb) ...
Unpacking replacement build-essential ...
[COLOR="Red"]dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev is not installed.
  Package libc-dev is not installed.
 build-essential depends on g++ (>= 4:4.1.1); however:
  Package g++ is not installed.
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not installed.[/COLOR]
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential
tom@emachine:~/debPackages$   

It couldn't install the package because of missing dependencies, as I understand this. However, I thought that's what "build-essentials" was supposed to provide.

What's the problem here? Any suggestions will be most welcome.

Thank you.

---

### Post by taurus on 2007-05-20
Insert the CD into the drive and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by Bachstelze on 2007-05-20
This is not the way to go. Do this

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo touch /etc/apt/sources.list
sudo apt-cdrom add
```

Insert your CD if you haven't already and press Enter. Then, when APT is done scanning it, do

```
sudo apt-get install build-essential
```

---

### Post by petersjm on 2007-05-20
(EDIT) Sorry, I should have read the full post! :(

---

### Post by tlinux on 2007-05-20
Your recommendations solved the problem! Build-essential is installed!

I really appreciate all of your help:D

---


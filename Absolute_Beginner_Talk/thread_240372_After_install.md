---
title: "After install"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by nemok on 2006-08-20
Hi,

New to Ubuntu (x64) and I have some questions:

1. What was that sudo command I should run after installing Ubuntu to delete 'oem' user and create new one?
2. Does Opera browser work on x64? And how?
3. I've just installed linuxdcpp but it doesn't work. It just says Starting DC++ in the task bar and then just closing without anything showing up. Is this because I am using x64? Any ideas?

---

### Post by catlett on 2006-08-20
```
sudo oem-config-prepare
```
that is to setup the account after oem

opera should work. the best way to get opera is to add the opera repo
ente4r this command ```
sudo gedit /etc/apt/sources.list
``` then add this to the file that opens
```
deb http://deb.opera.com/opera/ etch non-free
```Save and enter ```
sudo apt-get update
```
```
sudo apt-get install opera
```

I do not know anything about linuxdcpp

---

### Post by nemok on 2006-08-20
Thanks for your reply.

I have tried your solution for Opera but when I run sudo apt-get update I get:
```

Ign http://deb.opera.com etch Release.gpg
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Ign http://deb.opera.com etch Release
Get:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Ign http://deb.opera.com etch/non-free Packages
Hit http://us.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Err http://deb.opera.com etch/non-free Packages
  404 Not Found
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 3B in 1s (3B/s)
Failed to fetch http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
So I guess there is no x64 Opera version?
Any idea?

---

### Post by catlett on 2006-08-20
I do not know to tell you the truth. I do not run a 64 bit system. That is the repository for opera. I ran it before I gave it to you and it fetched opera9 32 bit compatable version. The error is either the repo didn't respond for some reason (down, maintenance) or it asked for 64 and it wasn't there. I'll search a bit and see if there is a definate answer for you

---

### Post by nemok on 2006-08-20
Thanks. Let me know if you find anything as I really like Opera and I want to use it on Ubuntu. Also I want to use the 64bit version of Ubuntu.

---

### Post by catlett on 2006-08-20
I am a bit surprised by Opera. As you can see by the link, they go out of their way to be as portable as possible [http://www.opera.com/download/index.dml?custom=yes](http://www.opera.com/download/index.dml?custom=yes) But it appears they do not support 64 bit in linux. Only i386.
You may want to install the 32 bit version of ubuntu buit install the 686-smp kernel. It has support for pentium dual processors. It is found in Synaptic
> Complete Linux kernel on PPro/Celeron/PII/PIII/PIV SMP.
This package will always depend on the latest complete Linux kernel available
for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV with SMP support.
SMP (symmetric multi-processing) is needed if you have multiple processors.
Or if you have AMD install 32bit ubuntu but install the k7 kernel
> Complete Linux kernel on AMD K7 SMP.
This package will always depend on the latest complete Linux kernel available
for AMD Duron/Athlon with SMP support.
SMP (symmetric multi-processing) is needed if you have multiple processors. It is a trade off. You have a 32 bit system that performs better than a regular 32bit with the right kernel although it isn't as good as running 64bit ubuntu but it supports more applications.

You may want to experiment. Create another partition and install 32bit ubuntu with the 686-smp kernel or the k7-smp and see how it compares. Or if you just installed, reinstal with the 32 bit.
Although 64bit architecture is the future and will be the standard, there are still many apps and hardware that aren't compatable. You may have to be imaginative until everything is ported to 64bit architecture. Good luck.

---


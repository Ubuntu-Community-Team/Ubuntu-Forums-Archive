---
title: "&quot;apt-get install libc6-dev g++ gcc&quot; while offline?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by frsrblch on 2007-09-18
I'm working with a clean install of Ubuntu, but I'm having great difficulty getting going here.  I'm living on campus now, so I need to authenticate with PuTTY to use the internet.  I have PuTTY downloaded, but I think I need the g++ and gcc compiler files so I can install from the source files (right?).  Anyway, I need to know where I can download those files, and how I can install them manually.

I have a dual boot set up, so I can only access the internet indirectly...

Much appreciated!

---

### Post by rajan on 2007-09-18
try burning the source onto a cd and then go to synaptic, and look for the "add cdrom" button under settings. otherwise you can probably change the URI to file///whateverthepathisyouwanttomake instead of the http path.



EDIT: 

oops, i didn't realize you were talking about putty in linux. is there a reason for this? if not, then try ssh ```
 which ssh
```. you can have X forwarding in ssh much easier than putty and i'm thinking that putty might be also written more for windoze than linux

---

### Post by Maestro23 on 2007-09-18
> **frsrblch said:**
> I'm working with a clean install of Ubuntu, but I'm having great difficulty getting going here.  I'm living on campus now, so I need to authenticate with PuTTY to use the internet.  I have PuTTY downloaded, but I think I need the g++ and gcc compiler files so I can install from the source files (right?).  Anyway, I need to know where I can download those files, and how I can install them manually.

I have a dual boot set up, so I can only access the internet indirectly...

Much appreciated!

You need the packages.  Using windows, go to Ubuntu Packages.

Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Download the packages you need (+ their dependencies) and save to a flash drive, cd, etc...

---

### Post by frsrblch on 2007-09-18
> **Maestro23 said:**
> You need the packages.  Using windows, go to Ubuntu Packages.

Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Download the packages you need (+ their dependencies) and save to a flash drive, cd, etc...

I'm downloading the packages, but it looks like I've run into a circular dependancy...

[http://packages.ubuntu.com/feisty/devel/g++-4.1](http://packages.ubuntu.com/feisty/devel/g++-4.1)
[http://packages.ubuntu.com/feisty/libdevel/libstdc++6-4.1-dev](http://packages.ubuntu.com/feisty/libdevel/libstdc++6-4.1-dev)

---

### Post by rajan on 2007-09-18
try this one:


[http://packages.ubuntu.com/feisty/devel/gcc-4.1](http://packages.ubuntu.com/feisty/devel/gcc-4.1)



gcc compilers include the c++ compiler package which is known as g++.

EDIT: here's the languages that gcc supports

[http://gcc.gnu.org/onlinedocs/gcc/index.html#toc_Standards](http://gcc.gnu.org/onlinedocs/gcc/index.html#toc_Standards)

---

### Post by pckong on 2007-12-09
> **frsrblch said:**
> I'm working with a clean install of Ubuntu, but I'm having great difficulty getting going here.  I'm living on campus now, so I need to authenticate with PuTTY to use the internet.  I have PuTTY downloaded, but I think I need the g++ and gcc compiler files so I can install from the source files (right?).  Anyway, I need to know where I can download those files, and how I can install them manually.

I have a dual boot set up, so I can only access the internet indirectly...

Much appreciated!

Hi,

I have the same problem!! 
While trying insall libc6-dev, I got linux-libc-dev is not installed.



 Any help would be greatly appreicated.

---

### Post by ruibernardo on 2007-12-10
Hi,

EDIT: **you can install those packages from the CD** (Alternate/Desktop or DVD) - check the next posts. The following info is just a list of the package files that are downloaded/installed on a [COLOR=Red]**Gutsy**[/COLOR] Desktop when you try to install the package names of the previous posts.

the following package files are for a not updated and  fresh install (if you don't have an internet connection, you haven't updated it) of Ubuntu **7.10 Gutsy** in a i386 computer (generic kernel, not 64 bits processor).

To install the package [build-essential]("http://packages.ubuntu.com/gutsy/devel/build-essential"):[INDENT][http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb)
[/INDENT]To just install [libc6-dev]("http://packages.ubuntu.com/gutsy/libdevel/libc6-dev") (a build-essential dependency):[INDENT][http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb)
[/INDENT]To install only [g++]("http://packages.ubuntu.com/gutsy/devel/g++") (also a dependency of build-essential):[INDENT][http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb)
[/INDENT]Both g++ or libc6-dev are included with build-essential packages. They both are dependencies of build-essential and are both installed if you just install all the packages of build-essential.

To install them, copy the files to an empty directory in the offline computer and install them with:
```
sudo dpkg -i *.deb
sudo apt-get install -f

```For other releases of Ubuntu (Feisty, Edgy, Dapper) or other non i386 processors (amd64, PPC, etc) and/or for other packages on the repositories check [this thread]("http://ubuntuforums.org/showthread.php?t=572819") or [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net) and create an account as described [here]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11") (you will need a file from the offline computer, but it will save you the time and confusion of searching all the dependencies of the packages in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)).

Good luck.

---

### Post by taurus on 2007-12-10
> **epimeteo said:**
> Hi,

the following package files are for a not updated and  fresh install (if you don't have an internet connection, you haven't updated it) of Ubuntu **7.10 Gutsy** in a i386 computer (generic kernel, not 64 bits processor).

To install the package [build-essential]("http://packages.ubuntu.com/gutsy/devel/build-essential"):[INDENT][http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb)
[/INDENT]To just install [libc6-dev]("http://packages.ubuntu.com/gutsy/libdevel/libc6-dev") (a build-essential dependency):[INDENT][http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb)
[/INDENT]To install only [g++]("http://packages.ubuntu.com/gutsy/devel/g++") (also a dependency of build-essential):[INDENT][http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb)
[/INDENT]Both g++ or libc6-dev are included with build-essential packages. They both are dependencies of build-essential and are both installed if you just install all the packages of build-essential.

To install them, copy the files to an empty directory in the offline computer and install them with:
```
sudo dpkg -i *.deb
sudo apt-get install -f

```For other releases of Ubuntu (Feisty, Edgy, Dapper) or other non i386 processors (amd64, PPC, etc) and/or for other packages on the repositories check [this thread]("http://ubuntuforums.org/showthread.php?t=572819") or [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net) and create an account as described [here]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11") (you will need a file from the offline computer, but it will save you the time and confusion of searching all the dependencies of the packages in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)).

Good luck.

But the build-essential package is on the installer CD.  So if you don't have a network connection, you can still install it with

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by maybeway36 on 2007-12-10
How do you authenticate with PuTTY? You could probably find some way to do it with built-in command-line tools.

---

### Post by ruibernardo on 2007-12-10
Hi Taurus,

yes it is on the Alternate CD or on the DVD. Those who have the Alternate CD or DVD don't need to download the packages.

 I'm guessing it's not the case here. If you only have the Desktop CD, you can't install it, I think. That listing is for an Ubuntu Gutsy Desktop install from a Desktop CD, which can't be used as a cd-rom repository and don't have build-essential.

Correct me if I'm wrong.

---

### Post by taurus on 2007-12-10
> **epimeteo said:**
> Hi Taurus,

yes it is on the Alternate CD or on the DVD. Those who have the Alternate CD or DVD don't need to download the packages.

 I'm guessing it's not the case here. If you only have the Desktop CD, you can't install it, I think. That listing is for an Ubuntu Gutsy Desktop install from a Desktop CD, which can't be used as a cd-rom repository and don't have build-essential.

Correct me if I'm wrong.

I haven't checked with Gutsy desktop CD (LiveCD) but it, build-essential, is on Feisty desktop CD.

---

### Post by ruibernardo on 2007-12-10
Oops, you are right, it is on the Desktop CD and can be installed from there. It just isn't installed by default during the installation and isn't present on a fresh install.

Sorry for misleading. I stand corrected and will edit my post. Thanks Taurus.

---


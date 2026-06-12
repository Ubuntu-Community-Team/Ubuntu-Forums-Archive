---
title: "install problems involving broken packes, help!"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by sysrpl on 2006-07-04
I am trying to install the toolkit lazarus-0.9.10-0.tar.gz and am having problems installing a few packages it requires. It requires the packages libgtk2.0-dev and libgdk-pixbuf-dev. 

When I try to install libgtk2.0-dev it goes something like this:

```
sudo apt-get install libcairo2-dev

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.2.0-0ubuntu1) but 1.0.4-0ubuntu1 is to be installed
E: Broken packages

/* I try this next */
sudo apt-get install libcairo2

The following packages have unmet dependencies:
  libcairo2: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2.1 is to be installed
E: Broken package

/* and finally this */
sudo apt-get install libfreetype6

libfreetype6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
What should I do? I really want to install the lazarus toolkit, but have no idea what to try next.

Many thanks if you can help.

---

### Post by Jagot on 2006-07-04
Not sure about your specific question, but I notice libcairo2 there and the recent update for it completely hosed my system today.  I don't know if there's anything wrong with the latest update in the repos or something, or it could just be my luck.

---

### Post by catlett on 2006-07-04
There is no guarantee that a tar file can be compiled into an application that will run on Ubuntu. The only sure way that an app Will work on ubuntu is if you find it in Synaptic Package Manager.
The next type of package that you should look for is deb files. These are debian files. Ub8untu is based on debian so the majority of deb files will install no problem.
A tar file is like rolling dice. Your system may be compatible. It may not. To put it in another context. It would be like trying to install a windows 98 program on xp, they are both windows and it is a windows application but it may not install. Same type of thing here. You are compiling a package that may have been meant to install on a system that has different linux libraries than ubuntu  libraries.
There are many different distros and they have different base libraries. Although they are similar, they may be just different enough to prevent you from installing.

The only advice I can give you is use aptitude instead of apt-get. It will try and resolve dependency issues better than apt-get. Just replace the wording apt-get in the command with aptitude.

---


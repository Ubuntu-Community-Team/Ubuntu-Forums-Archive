---
title: "Initialising HFS+ from installer"
date: 2006-09-05
forum: Apple PPC Users
---

### Post by kulath on 2006-09-05
Is it possible to create and initialise and HFS+ partition from within the installer.

The built in partitioner does not offer HFS or HFS+ as as option.

parted seems to be able to change the size of an HFS+ partition successfully, but not create one (or is it only create one without initialising it).

mac-fdisk asks for a partition type, but the man page does not seem to specify what are valid values, and I don't know how to specify HFS+ as opposed to HFS, and does it initalise?

(I want to persuade the installer to mount the partition as /home, after I have created a Linux and swap partition, and don't want to go back out to booting from the Mac OS X installer disc just to initialise the partition).

---

### Post by kulath on 2006-09-10
Just touching this to try to get an answer.

> **kulath said:**
> Is it possible to create and initialise and HFS+ partition from within the installer.

The built in partitioner does not offer HFS or HFS+ as as option.

parted seems to be able to change the size of an HFS+ partition successfully, but not create one (or is it only create one without initialising it).

mac-fdisk asks for a partition type, but the man page does not seem to specify what are valid values, and I don't know how to specify HFS+ as opposed to HFS, and does it initalise?

(I want to persuade the installer to mount the partition as /home, after I have created a Linux and swap partition, and don't want to go back out to booting from the Mac OS X installer disc just to initialise the partition).

---


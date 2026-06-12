---
title: "loop mounted install"
date: 2012-01-31
forum: Any Other OS
---

### Post by sc0ttman on 2012-01-31
I am a user of Puppy Linux, which can be installed as a loop mounted file system 
(squash filesystem file decompresses [entire] filesystem into RAM, at boot)
and Puppy Linux once again supports 'underdog linux' installs.

If you don't know, loop mounted filesystems can be mounted on top of each other.
You can have different filesystems mounted and layered upon each other as one.

The 'underdog linux' feature of Puppy Linux lets you use any distro as the bottom layer,
and all Puppy filesystem stuff (and addons, tmpfs stuff, etc) is loaded on top..

This means Puppy can essentially be run on top of other distros..
Here is the quote from the developer, Barry K:

> File underdog.lnx is just a text file, containing the name of a partition, for example "hda1". At bootup Puppy will read underdog.lnx and will mount the partition as the bottom layer. If that partition happens to have a Linux distro installed in it, then the entire distro filesystem will "show through" on the top layer of Puppy's unionfs.

 It will look like a normal Puppy Linux ... but everything in the underlying distro is available to be executed. All the applications, compile environment, package manager, etc.

More info  --->  [http://bkhome.org/blog/?viewDetailed=02668](http://bkhome.org/blog/?viewDetailed=02668)

The 'underdog' could simply a very limited, console only, version of Ubuntu, 
with a working package manager.. Thus giving any Puppy full apt-get support, etc... 

My questions are thus:

1. What is the smallest Ubuntu remix/derivative/spin-off/whatever that includes the full package manager, and working access to large repos?

2. Which Ubuntu works best with glibc 2.10.1?

Cheers

---

### Post by sc0ttman on 2012-02-11
bump

---


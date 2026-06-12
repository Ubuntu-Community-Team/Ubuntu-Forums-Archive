---
title: "downloading make"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by James0044 on 2006-08-26
Hi,

I'm trying to install ndiswrapper, but to do this i need a command called 'make' which does not appear to be on Ubuntu Dapper. I have found a place where i can download it (using my XP PC, as my Ubuntu PC does not have net), but i have no clue which file i need, there are about 20, do i need them all?

I have an old pentium 3 1.6ghz.

Here is the link.

[http://archive.ubuntu.com/ubuntu/pool/main/m/make/](http://archive.ubuntu.com/ubuntu/pool/main/m/make/)

Thanks

---

### Post by %hMa@?b&lt;C on 2006-08-26
sudo aptitude install build-essential
try running that in termial

---

### Post by lynxus on 2006-08-26
make should be installed! ?

try running teh command as root as sometimes it will say the command / program doesnt exsist if its run as user.

---

### Post by James0044 on 2006-08-26
Thanks, tried running that command, some writing came up on the screen ending with can not find programme 'build-essentials'. tried the make command again, but still no joy.

also tried writing the command as root, using the sudo command, but that didn't work either. any ideas?

---

### Post by James0044 on 2006-08-26
I read a post written a while back that said make was not installed on dapper.

---

### Post by MrHorus on 2006-08-26
```
sudo apt-get install build-essentials
```

or build-essential - I can't remember which one it is but ONE of them will work :)

---

### Post by az on 2006-08-26
build-essential and linux-headers and everyting you need is on the install cd.

On the Desktop (live) cd, those packages are on a repository apart from the live session.  Just boot your computer normally and when at the gnome desktop, insert the cd.  The package manager will detect the repository and start - you will thenbe able to install those packages.


Just install ndiswrapepr-utils - it is in that repo as well.  You most probably do not need to recompile ndiswrapper.

---

### Post by cstudent on 2006-08-26
Make is not installed by default. You have to add the build-essential package.

See this post on how to get and install the build-essential package

[http://www.ubuntuforums.org/showthread.php?t=244292](http://www.ubuntuforums.org/showthread.php?t=244292)

---

### Post by James0044 on 2006-08-26
Thanks, I just had a go, it told me…

Reading package lists…done
Building dependency tree….done
E: couldn’t find package build essential/s

A couple of things that you might want to know…

I am doing all this in my use space: james@james-desktop:-/ndiswrapper1.23$
And I don’t have the net on my ubuntu computer.

Sorry to be a pain.
Any other ideas?

---

### Post by James0044 on 2006-08-26
Wow, that worked!

Installed everything from the CD, and i've learnt a few things along the way, just have to install the network card now.

Thanks all!
James

---


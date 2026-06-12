---
title: "[SOLVED] dpkg was interrupted (now stuck in a loop)"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by bornagainpenguin on 2008-04-03
Reposting this here in hopes of getting help more quickly....I have already posted in the zen kernel [thread]("http://ubuntuforums.org/showpost.php?p=4646515&postcount=526") as well though...

Before anyone asks why I didn't just type the commands into terminal, please note that I *did* and read on for the second error message, which is where I am currently stuck.  I don't even have the zen kernel installed anymore so..... :confused:

> **bornagainpenguin said:**
> Trying to update Ubuntu gets me this error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Trying to run those commands in terminal gets me this response:

```
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-zen1-x86
Cannot find /lib/modules/2.6.24-zen1-x86
update-initramfs: failed for /boot/initrd.img-2.6.24-zen1-x86
dpkg: subprocess post-installation script returned error exit status 1

```

And then dumps me back out to the command line.  Any ideas how I can fix this?

--bornagainpenguin

PS: NOTE: I am using an older build of zen.

....anyway.... any ideas?  I'd really rather not have to do a fresh install so close to the release of Hardy Heron.....

--bornagainpenguin

---

### Post by Inxsible on 2008-04-03
and you did use sudo on the command right?


......just checking

---

### Post by Hospadar on 2008-04-03
what if you try uninstalling those packages first, then updating, then reinstalling them?  If you don't purge them, their configuration files should stay behind

---

### Post by Lord Illidan on 2008-04-03
I came into your issues once. A quick way of fixing it was making a directory with ```
sudo mkdir /lib/modules/2.6.24-zen1-x86
```However, I then promptly removed the package, as it didn't work for me.

---

### Post by bornagainpenguin on 2008-04-03
> **Inxsible said:**
> and you did use sudo on the command right?


......just checking

#-o  Very funny!

> **Hospadar said:**
> what if you try uninstalling those packages first, then updating, then reinstalling them?  If you don't purge them, their configuration files should stay behind

As far as I know the packages should have been purged.  I used the complete removal option in Synaptic, so.... :?:

> **Lord Illidan said:**
> I came into your issues once. A quick way of fixing it was making a directory with ```
sudo mkdir /lib/modules/2.6.24-zen1-x86
```However, I then promptly removed the package, as it didn't work for me.

=D> Thank you! This worked for me!  AFAIK I'd already uninstalled these packages awhile ago, so... :confused:

--bornagainpenguin

PS: How does one mark an issue as solved? <=== Never mind I found it!

---


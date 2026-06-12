---
title: "Completely uninstalling Perl"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by DangerMouse1981 on 2008-04-01
Hi all,

Complete linux beginner here so bare with me; I'd like to completely uninstall Perl from my JeOS 7.10 install, to be replaced by a fresh compile directly from the Perl binaries.

I've noted in other threads that removing Perl isnt recommended so I'd appreciate some advice as to how to go about this? My motivation is a PHP extension that makes use of the Perl libraries refuses to function - thus I need to completely eliminate Perl as my weak link before attempting another distro.

Cheers,

DM

---

### Post by Cypher on 2008-04-01
Perl is used by various applications in the Linux system and attempting to remove the packages will be met with depdency failures from other packages. You're best bet is to compile your new Perl code the way you want it and create DEB's. Now overwrite the existing Perl installation with your DEBs and then go into Synaptic and PIN the Perl packages you installed so that they dont' get overwritten by the normal Ubuntu upgrade process..

---

### Post by DangerMouse1981 on 2008-04-01
Thanks for the reply Cypher. I'm really new to Linux so a few things there kind of lost me I'm afraid, it would be great if you could clarify.

DEB - install files yeah? How would I go about generating them from the Perl compile (is this after "make" is run?)

Synaptic and PIN - no idea what this is sorry, sounds like a package manager? I've only used apt-get to install packages so far, or compiled things from downloaded archives.

Cheers,

DM

---


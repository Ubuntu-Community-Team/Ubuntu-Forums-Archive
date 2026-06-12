---
title: "Authenticate OS X users from Ubuntu"
date: 2005-09-04
forum: Apple PPC Users
---

### Post by chrisphin on 2005-09-04
Hi all

I've got a dual boot (Hoary + Mac OS X 10.3) set up on an old G3, and have finally managed to work out how to mount the OS X parition in Ubuntu.

(A bit of background: I'm a very compenent Mac OS X user - in GUI, not Terminal - but Linux is pretty new to me)

When I navigate to my regular OS X user while booted into Ubuntu, permissions deny me access to all but the Public and Sites folder. I'd expect this (obviously the same thing happens if I try to access my data from another OS X user regardless of partition), but wanted to know if there was any way to authenticate me in Linux to open those folders, as I obviously know my login details for that OS X user.

It's no huge problem; I'm just playing with Linux at this stage to learn about it, and I can always use the Public folder, but I was curious to know if there was a way round this.

Many thanks, all.

---

### Post by chrisphin on 2005-09-04
It occurs to me that perhaps I need to authenticate specifically as my OS X user when I enter the mount command in Ubuntu's Terminal, as one does when connecting to another volume in Mac OS X. If this is the case, what command do I need to add to my mount command (which, until someone tells be otherwise, is "mount /dev/hdc11 /mnt/macosx -t hfsplus")

Thanks

---

### Post by nickfull on 2005-09-09
[QUOTE=chrisphin]Hi all

I've got a dual boot (Hoary + Mac OS X 10.3) set up on an old G3, and have finally managed to work out how to mount the OS X parition in Ubuntu.

(A bit of background: I'm a very compenent Mac OS X user - in GUI, not Terminal - but Linux is pretty new to me)

When I navigate to my regular OS X user while booted into Ubuntu, permissions deny me access to all but the Public and Sites folder. I'd expect this (obviously the same thing happens if I try to access my data from another OS X user regardless of partition), but wanted to know if there was any way to authenticate me in Linux to open those folders, as I obviously know my login details for that OS X user.

It's no huge problem; I'm just playing with Linux at this stage to learn about it, and I can always use the Public folder, but I was curious to know if there was a way round this.

Many thanks, all.[/QUOTE]


on this thread [http://ubuntuforums.org/showthread.php?t=4411&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=4411&page=1&pp=10) there is info which should help you do this in fstab... i've not got it work for me but others have reported success with it. good luck!

---

### Post by stuporglue on 2005-09-24
[QUOTE=chrisphin]Hi all
When I navigate to my regular OS X user while booted into Ubuntu, permissions deny me access to all but the Public and Sites folder. I'd expect this (obviously the same thing happens if I try to access my data from another OS X user regardless of partition), but wanted to know if there was any way to authenticate me in Linux to open those folders, as I obviously know my login details for that OS X user.
[/QUOTE]

The easiest way to not worry about permissions is to make your uids the same on linux as on OSX. It's probably easiest to create a new user on Linux, since the Ubuntu Users manager lets you pick a uid, I believe. If you've got a matching uid, you'll be able to enter those folders. 

If you need multiple people to access them, that's more trouble....

---


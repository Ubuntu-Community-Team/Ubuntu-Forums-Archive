---
title: "Dual booting ubuntu on powerpc mac"
date: 2008-10-17
forum: Apple Hardware Users
---

### Post by krazykeith250 on 2008-10-17
I just bought a ubuntu 7.04 disk for like $5, but the only thing is, after I bought it I saw all this stuff about a thing called yaboot and I was wondering if I need to get yaboot if I want to dual boot a powerpc mac, or can I just make a partition at the inatallation and when it boots just hold down the option key like you can on intel macs?

I am very new to ubuntu and need some help.

Thank you.

---

### Post by MikeTheC on 2008-10-18
This is an interesting proposition and challenge, so I'll start.

First off, you need to know whether your Mac is a so-called "Old World ROM" or "New World ROM" Mac. Basically, any of the Blue and White G3 or newer towers are "New World ROM" Macs, along with any of Apple's laptops starting with the iBook G3 clamshell units.

Anything older than that are "Old World ROM" systems which require something of a juggling act to get set up.

Do you want this system dual-booted between Mac OS and Linux? If you do, it's best to nuke-n-pave the system on the Mac side and use a setup utility on the Mac to do the initial partitioning, putting (as a "best practice") the Mac OS-using partition first, and leaving the rest of the drive as what's called "unallocated space".

If, on the other hand, you want to use the entire HDD for Linux, then you should be able to boot the CD (again, assuming it's a NWR system) and just tell the installer, once you're at the hard drive partitioning portion, to just use the entire drive for Linux.

Good luck!

---

### Post by oswaldkelso on 2008-10-18
[http://www.my2bits.org/?s=yaboot](http://www.my2bits.org/?s=yaboot)

If you search yaboot on the forums here or in the ppc archive you should find some more info

---

### Post by krazykeith250 on 2008-10-18
I thought that in the ubuntu install it gives you an option to partition the hard drive right there in the installation.

---

### Post by tiresia on 2008-10-18
If you boot from the LiveCD, you can use GParted to resize an HFS+ partition (Mac OS)
But you should backup your data!!!

---


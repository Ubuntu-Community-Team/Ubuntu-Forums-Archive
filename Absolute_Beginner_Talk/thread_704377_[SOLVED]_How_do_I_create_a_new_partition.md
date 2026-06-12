---
title: "[SOLVED] How do I create a new partition?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Taum on 2008-02-22
I have a computer that only has Ubuntu on it, but I need to create a partition to put  Windows on for a couple of work related programs and I have no idea of how to go about doing that.  I tried the Disk Usage Manager for the first time, and while it doesn't do jack for partitioning, it's a really cool GUI for disk info.  Anyhow, if there's a utility or line command that will work, lemme know.

I'm a novice on Linux, so please explain this to me as if this is my first computer.  Thanks.

---

### Post by taurus on 2008-02-22
Download and burn GParted LiveCD and use it (boot from it) to resize your harddrive.  You cannot resize your harddrive while you are using it.  Have to be done from a LiveCD.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

As always, back up your important data on Ubuntu before you start in case something goes wrong.

---

### Post by ajgreeny on 2008-02-22
Or if you have a ubuntu live CD you can use the gparted in that without bothering to download another lot of software.  Just remember that if the ubuntu you have already installed is mounted you will not be able to work on it, so if the live CD mounts it automatically, right click on the appropriate partition in gparted, select unmount, and you should be ready to go.  Just make sure you backup all important files first, just in case.  I've never lost anything, but it is always possible.

---

### Post by Taum on 2008-02-22
I have the Ubuntu 6.10 disc, does that have the appropriate software on it?

---

### Post by Duck2006 on 2008-02-22
> **Taum said:**
> I have the Ubuntu 6.10 disc, does that have the appropriate software on it?

Yes it has gparted on it.

---

### Post by kooolrock on 2008-02-22
> **Taum said:**
> I have the Ubuntu 6.10 disc, does that have the appropriate software on it?
plz ugrade!!!

---

### Post by Taum on 2008-02-22
I'm running Gutsy, I only have the disc for 6.10 though.

---

### Post by Taum on 2008-02-22
Oh, and GParted worked like a Charm!  Now if I can only figure how to keep Windows from being the only OS that will start up.  It's either a Windows setting that they hide from you, or a BIOS thinger.

---

### Post by ShodanjoDM on 2008-02-22
> **Taum said:**
> Oh, and GParted worked like a Charm!  Now if I can only figure how to keep Windows from being the only OS that will start up.  It's either a Windows setting that they hide from you, or a BIOS thinger.

Sounds like you need [Super Grub Disk]("http://supergrub.forjamari.linex.org/")

---

### Post by Taum on 2008-02-23
> **ShodanjoDM said:**
> Sounds like you need [Super Grub Disk]("http://supergrub.forjamari.linex.org/")

Thanks!  That did the trick!

---


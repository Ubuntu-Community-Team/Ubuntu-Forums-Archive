---
title: "Problem Installing Ubuntu - No root file system"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by brey493 on 2007-01-21
Trying to install ubunto on a macbook pro.  after preparing partitions i get no root file system.  any help would be appreciated.

---

### Post by jem7v on 2007-01-21
What version of Ubuntu are you trying to install, and what install CD are you using (i.e., LiveCD, Alternate, Server, etc)?

---

### Post by nelsland on 2007-01-21
i just intall it a few days ago

make sure when you assign 2 partition to the install
one has a file system of ext3
and one has a file system of linux-swap

then on the next page, make sure that ext3 partation (you new root drive) has a "/" on the left side

then the partition with "linux-swap" assigned as "swap" on the left side

that should work, what how i got my set up

---

### Post by brey493 on 2007-01-21
trying to install 6.10.  Fedora 6 installs just fine so I can't figure out what is wrong.

---

### Post by brey493 on 2007-01-21
im using the cd from linux format

---

### Post by ghevan on 2007-01-21
I had a similar problem with xubuntu 6.10, I kept getting the message of no root file system.  My problem was that I made the partitions with hiren's boot, so to fix it I had to reformat using the gparted that comes within the live CD to make it all work.

---

### Post by jem7v on 2007-01-22
There Are some known issues regarding root file systems and some of the 6.10 LiveCD installers.  There's a brief overview of them in the 6.10 release notes here:
[http://www.ubuntu.com/download/releasenotes/610#head-ffc2b2285bd1df460d1ff8aa353c716f9151ceb2](http://www.ubuntu.com/download/releasenotes/610#head-ffc2b2285bd1df460d1ff8aa353c716f9151ceb2)

---

### Post by rleon on 2007-02-02
I had the same problem with the Ubuntu installer. But the solution is easy: just go back to the partition manager, delete and recreate the partition that is going to be root. Then you can go ahead.

---

### Post by FlJim on 2008-01-19
Yeah, first you have to delete the partition
then create the root
then the swap
both are primary
don't forget the "/"

Has to be in that order

---


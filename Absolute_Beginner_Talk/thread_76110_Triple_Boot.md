---
title: "Triple Boot"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by freewalker on 2005-10-14
In setting up a triple boot system, one for XP(games), one for linux, and another for linux for testing.  Can I run that setup with only one swap partition?  Thanks for any info all.  What about /home.  Can I run them with one /home partition?  Thanks for info all.

---

### Post by Kapre on 2005-10-14
[QUOTE=freewalker]In setting up a triple boot system, one for XP(games), one for linux, and another for linux for testing.  Can I run that setup with only one swap partition?  Thanks for any info all.  What about /home.  Can I run them with one /home partition?  Thanks for info all.[/QUOTE]

freewalker - yes you can use only 1 swap (I'm using only one for quad boot).

K

---

### Post by Wolki on 2005-10-14
[QUOTE=freewalker]In setting up a triple boot system, one for XP(games), one for linux, and another for linux for testing.  Can I run that setup with only one swap partition?  Thanks for any info all.  What about /home.  Can I run them with one /home partition?  Thanks for info all.[/QUOTE]

You can use one swap for all of them, but if you hibernate in one and boot another, the hibernated state will be overwritten.

You can use only one home directory, but unless you run the same versions of programs on both linuxes I would be careful. Some programs might not like having a configuration file of a later version.

You can create two small /home directories and a third partition for non-configuration file date, then create links into the home partitions so you have the same emails etc. between both linuxes.

---


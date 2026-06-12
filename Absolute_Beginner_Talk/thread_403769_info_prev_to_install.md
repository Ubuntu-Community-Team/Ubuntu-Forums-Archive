---
title: "info prev to install"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by blade_2000 on 2007-04-07
hello to everybody,
before installing ubuntu (before partitioning actually), i'd like to know a couple of things:
1) how much space should i reserve for ubuntu and how much partitions? from the docs i've understood a root partition of 5gb and a swap partition
2) what kind of swap filesystem does it use? (i'm going to install other distros, such as suse 10.2, fedora 7 and maybe gentoo later) for comparison and learning purposes and i'd like to use just one swap partition for all of these if possible)

in answering please consider that i'm referring to ubuntu 7.04 (when it's out) and that i don't really need much more space than initial install 'cause i'm not going to download a lot of progs, so i just need to know the space for a (maybe full) install

thanks

---

### Post by chamberlain2006 on 2007-04-07
The root partition only really needs to be a couple GB, (5gb will be enough).  The swap partition is the same as with most distros; they can share the same one.  If you are going to be using other OS's, you should have another partition where they can share documents and files.  If you are going to be using Linux, this should be in ext3 format.

---

### Post by userundefine on 2007-04-07
1.  After about a year, my root is sitting at 5.5GB in used space.  I've got /home on a separate partition.  If you're installing mysql, php, apache, maybe games, I'd recommend more than 5.

2. You can share a swap partition between all distros.  There is really only one type of "swap", unless you're distinguishing between swap as a partition and swap as a file.  They're all the same filesystem.

---

### Post by justin whitaker on 2007-04-07
> **blade_2000 said:**
> hello to everybody,
before installing ubuntu (before partitioning actually), i'd like to know a couple of things:
1) how much space should i reserve for ubuntu and how much partitions? from the docs i've understood a root partition of 5gb and a swap partition
2) what kind of swap filesystem does it use? (i'm going to install other distros, such as suse 10.2, fedora 7 and maybe gentoo later) for comparison and learning purposes and i'd like to use just one swap partition for all of these if possible)

in answering please consider that i'm referring to ubuntu 7.04 (when it's out) and that i don't really need much more space than initial install 'cause i'm not going to download a lot of progs, so i just need to know the space for a (maybe full) install

thanks

You really only need 2 partitions: / and swap. I would say that 5gb is sufficient for a stripped down system, but if you want to actually play around with the systems and applications, start looking in the 10-20gb range. You need at least double available RAM for the swap file (you can get away with less).

---

### Post by blade_2000 on 2007-04-07
thanks for the answers
that's what i needed to know

and i have to say this is the quickest forum i've ever posted to, 3 answers i 5 mins! :)

---

### Post by zvacet on 2007-04-07
Belive me,you need home partition.That partition saves your data and settings.In case of reinstall,fresh install or something else you will overwrite just root partition ans home will stay intact.After you decide how much space you will give to root and swap give the rest to the home.

---


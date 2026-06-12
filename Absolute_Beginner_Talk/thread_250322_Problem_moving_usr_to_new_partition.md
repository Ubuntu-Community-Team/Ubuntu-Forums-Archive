---
title: "Problem moving /usr to new partition"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by markde25 on 2006-09-03
Hi Folks,

I am trying out Ubuntu for the first time, but have some experience with other Linux distros.  I have a very small (test) system setup which I wanted to use to learn about Ubuntu before migrating my main box to it.  The test system has a "very" small hard disk which is almost out of space (about 2 GB), so I dropped in an old 20 GB disk (fdisk'ed it, formatted, etc.) with the intent of mounting one partition on it at /usr.

I booted the system using a DSL (D*mn Small Linux) live disk and mounted the old hda1 and the new hb1 parititons.  I then ran:
```

$ cd /mnt/hda1/usr
$ cp -a * /mnt/hdb1
$ mv /mnt/hda1/usr /mnt/hda1/oldusr
$ mkdir /mnt/hda1/usr

```

I made the changes in /etc/fstab and restarted the system.  There are two things I noticed after getting up and running in Ubuntu again.  (1) My "Applications" menu was missing and (2) issuing the du -s command reports over 100 MB of difference between the "oldusr" directory and the files stored on hdb1.

I re-created the applications menu and everything seems fine, but I am a bit concerned that the installation will break later as a result.  :neutral: 

Does anyone know why the total size would be different after such a copy command?  Could it be that the cp dereferenced some of the symlinks even though -a was specified? :???:

Thanks in advance for any help or ideas! :)

---

### Post by kidders on 2006-09-04
Which version is bigger?

Afaik cp -a (cp -dpR) doesn't ever dereference symbolic links. One possible explanation that jumps to mind is that you might not be using the same filesystem in both places (which can affect the reported size of empty directories, for example) or maybe chose a different block size.

How about trying **diff /usr1 /usr2** to try to convince yourself everything is okay?

I doubt this applies to /usr directories, but I'm not altogether certain **cp * ...** copies dotfiles. Idiotic suggestion? Thought so!

If *I* were going to move my /usr, I'd do an **lsof | grep /usr** first, just to be sure nothing important was open, but that's maybe a bit paranoid. Post back if you track down what happened ... I'm curious! A broken applications menu is concerning :(

---


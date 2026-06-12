---
title: "Error loading Synaptic Pkg Mgr on Asus Eee PC901"
date: 2011-11-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by iluminameluna on 2011-11-05
I'm using a Live USB w/ Lubuntu Oneiric 'cause I'm having issues installing using 2 SSDs. Thread on Linux Questions Forum.

However, after downloading the Alternate version of LOneiric 11.10, I wanted to create a Live USB of it.

However, the Live USB version of Lubuntu won't run the Synaptic Package Manager. I get an error window that gives me this:


> E: Unable to synchronize mmap - msync (28: No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I'm running on 2G of RAM.

I tried > ubuntu-bug Synaptic Package Manager in the Run window. Nothing happened.

I'm running the Task Manager & can't decipher which process belongs to the Syn Pkg Mgr.

I feel like I'm walking down a maze in a garden. Every turn offers me another block to trying to do something I've done w/ every other Ubuntu pkg until Ubuntu Ntbk Remix: do a manual install so I can tell the OS where to put what ...

Help!

---

### Post by drs305 on 2011-11-05
Part of your error messages include
> E: Unable to synchronize mmap - msync (28: No space left on device)

A full partition can result in a variety of problems. You can check if the disk is full with
```
sudo df -Th
```

You can probably get enough space if "/" is showing full (100%) by emptying your own Trash bin and also the cached packages, which you don't need:
```
sudo apt-get clean
```

Try those commands and see if you can now install Synaptic.

If the problem *was* due to the partition being full, you should then investigate why your partition is full. Here is a thread that might help.
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---


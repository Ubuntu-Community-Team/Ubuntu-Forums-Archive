---
title: "Installing Ubuntu without formatting partition"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by acheron on 2006-10-04
Is there any way to install Ubuntu to an existing ext3 partition without reformatting the partition? I manually removed all the directories from the previous installation (except /home) only to find that the installer doesn't allow to skip this step. I have Kubuntu-6.06.1-desktop-amd64. I just don't want to repartition, because last time I tried that, many file names got garbled.

---

### Post by shanepardue on 2006-10-05
yeah, you'd need to format. is there a reason you don't want to format? backing up isn't too hard.

---

### Post by acheron on 2006-10-05
>backing up isn't too hard.

Backing up >30 Gb of scanned Guinier diffractogramms is. :) Additionally about half of file and directory names got damaged after a resizing attempt, and I'll have to sort them first, which is easier to do with a well-running GUI, which was the reason to switch from Debian to Ubuntu in the first place -- newer and MUCH better drivers for my video :) 

Besides I don't have that many CD's at hand :)

It is possible to install Ubuntu from a Knoppix LiveCD with working network. Is it so much harder to do this from Kubuntu LiveCD but without network? Any suggestions, links? 

Google gives too many, but nothing relevant, it seems.

---

### Post by shanepardue on 2006-10-05
why not create a new partition for storage making two total partitions then format the one for installing ubuntu.

---

### Post by acheron on 2006-10-05
What advantages does a 2-disk system have? The only disadvantage is the risk of losing the data. :) Not much of a disadvantage, but enough for me. :) That's why I'm asking.

AFAIK reformatting isn't really needed, it's just there to be on the safe side. Only some Red Hat distributions demand it, all others do fine without. Unfortunately, only Ubuntu works fine with my hardware, others give a choice between 1280x1024@60Hz and text mode.

---

### Post by jaboua on 2006-10-05
There are lots of advantages, for example:
- /home can be kept separate from /, making it easier to migrate between distros or reinstall
- As often written-to files in for example /var are kept away from /home, there will be less fragmentation on /home
- Less chance for the /home to be corrupted during powerloss because of some metadata changes in other parts of the filesystem

But as you say, I believe that ubuntu should work fine without reformatting the drive since you wiped out the other distro's files - however to skip the formatting part of the installer you might have to edit the installation application itself.

---

### Post by dannyboy79 on 2006-10-05
You don't need to format!!!! When you go through the installation, there is an option within the manual partition setup that states to format or not!!!

---

### Post by jaboua on 2006-10-05
> **dannyboy79 said:**
> You don't need to format!!!! When you go through the installation, there is an option within the manual partition setup that states to format or not!!!
I believe I tried disabling the formatting option in kubuntu installer but it said that it had to format it

---

### Post by crokett on 2006-10-05
If you run the text mode install you can specify whether to format or not on non-swap partitions. swap must be formatted. text mode gives much more control over your partitions - what is formatted, what is mounted, mount points, etc. I prefer text mode.  much faster and a bit more control.

---

### Post by acheron on 2006-10-05
I was hoping to find something like a list of scripts to run manually. Anyway, I won't have time to try until Saturday.

---


---
title: "Reinstall help"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-02-09
Okay, long story short, I've screwed the pooch.  I've broken several programs, I can no longer burn CDs, edit menus, or start gdesklets.  Rather than work my way back to stability, I'm just going to reinstall.  I think it's the better option anyway; now that I've been using Linux for a while and I'm more aware of "good housekeeping" practices, it seems way easier to start fresh and keep it clean than try to clean everything up in my present installation.

So, I'm just going to bite the bullet and do it.  I've made a list of applications to reinstall when I'm done.  I've backed up my data (media & docs), I've backed up my fstab and my sources.list (which were two major pains when I first installed).  Are there any other config files that I would do well to keep, or, in general, anything I should keep in mind before I wipe the partition?  I don't want to go into this half-assed.  Anyone who's done this before, your advice is totally appreciated.

---

### Post by Sutekh on 2006-02-09
I'd backup your apt cache, to save you downloading all those packages again.

[Ubuntu Starter Guide - Howto backup/restore downloaded repositories cache?]("http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache")


Plus anything in hour home folder that is in hidden directories, like firefox extensions and bookmarks.  I'll scrape up a link for doing that.

[http://www.ubuntuforums.org/showpost.php?p=531809&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=531809&postcount=4")

---

### Post by TeeAhr1 on 2006-02-09
Thank you for the advice, but I'd better not.  I think some of those packages are causing the problems I'm having (conflicting libraries?).

As a curiousity, though, does the restore there completely reinstall the packages, or just back up the deb files?

---

### Post by Sutekh on 2006-02-09
No it only backs up the *cache* of .debs.  It will untar the backup.tar to the apt cache folder.  You don't have to install them again, and you can always delete those you don't want. 

For me I would rather not have to download some of the big ones, like new kernels, wine, etc.

---

### Post by TeeAhr1 on 2006-02-09
Okay, if I understand correctly, when I untar the file, it doesn't install the debs, but when I apt-get install those packages, it will pull them from there instead of downloading them?

(sorry if this seems elementary...)

---

### Post by Sutekh on 2006-02-09
Yes thats correct the untar, puts your old .debs into /var/cache/apt/arhives.

When you use apt-get to install a package that is in that folder, it won't have to download it.

If you are worried about packages/dependencies then delete the offending packages from this folder before using the tar command.

Or delete everything *except* those package you *know* you will need again.

---

### Post by TeeAhr1 on 2006-02-09
Hey, thanks a lot.  This is teh good advice right here. :D

---


---
title: "[SOLVED] kde desktop"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-10-14
I currently have ubuntu 7.10, and plan to upgrade (or clean install kde)  when Gutsy becomes available.  Question... Should I do a clean install of kde, or just upgrade? I am using the kde desktop now (as well as gdm). I really don't need both desktops, but don't know what to do.:confused:

---

### Post by forestpixie on 2007-10-14
Ubuntu 7.10 is Gutsy ;)

If you've got both dekstops installed and want to clear one out completely then I'd be inclined to do a clean install

---

### Post by Capricori on 2007-10-14
Either way should work. Although, if you upgrade whilst having KDE and GNOME installed, I assume it would have to download more packages, so the upgrade would take longer.
You can find instructions for removing Gnome (leaving you with pure Kubuntu) at [the psychocats site]("http://www.psychocats.net/ubuntu/purekde")

---

### Post by skyjacker on 2007-10-14
> **forestpixie said:**
> Ubuntu 7.10 is Gutsy ;)

If you've got both dekstops installed and want to clear one out completely then I'd be inclined to do a clean install How would I do a "clean install"? I dual boot  (for a few more months) with Windoz Xp.  Here is what my HD looks like now:
/dev/hda1  NTFS
/dev/hda2  Fat32
/dev/hda3  Linux
/dev/hda4  Extended
/dev/hda5  Linux Swap
P.S. Idont want to lose XP just yet. Thanks for your help.:)

---

### Post by forestpixie on 2007-10-14
when you run the install you just need to point it at the right partitions, which would appear to be hda3 for /, and hda5 for swap - the same as it is now. I fou've got data you need to keep make sure you have a backup because a clean install will lose your /home as it's not separate.

---

### Post by skyjacker on 2007-10-14
> **forestpixie said:**
> when you run the install you just need to point it at the right partitions, which would appear to be hda3 for /, and hda5 for swap - the same as it is now. I fou've got data you need to keep make sure you have a backup because a clean install will lose your /home as it's not separate. Thanks for your help. I'll mark this thread as solved!

---


---
title: "HFS+, disabled journaling, still can't r/w"
date: 2009-03-20
forum: Apple Hardware Users
---

### Post by jackbusch on 2009-03-20
I  swear I disabled journaling - I opened up disk utility in OS X and clicked DISABLE journaling. But when I try to mount it in Ubuntu, I get :


Mar 20 06:31:02 jakc-laptop kernel: [ 1510.743691] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.


Do I need to re-format and re-partition the hard drive from scratch in order for Linux to believe that its not journaled?

Also, when I browse the hard drive, I can look at most folders, but others (my iTunes folder, for example) are inaccessible.

---

### Post by cyberdork33 on 2009-03-20
> **jackbusch said:**
> I opened up disk utility in OS X and clicked DISABLE journaling.
That sometimes happens. Use the command:

```
diskutil enableJournal /Volumes/TheVolumeName
```
to enable it again, then disable with:
```
diskutil disableJournal /Volumes/TheVolumeName
```
then try again.

> **jackbusch said:**
> Also, when I browse the hard drive, I can look at most folders, but others (my iTunes folder, for example) are inaccessible.
that is a permissions issue. Linux respects the set permissions of files and folders on HFS+ volumes. your Ubuntu user does not "own" those files, and the permissions are set to disallow access to those that do not own them. Boot into OSX and place files in a different location that has full access, or change the permissions of your music folder to allow access to others.

---

### Post by jackbusch on 2009-03-21
Ah, okay - well, Ubuntu still thinks its journaled. But that's okay because now I can at least read from there (thanks to the permissions tip) which is what I really wanted. Thanks!

---

### Post by weberc2 on 2012-03-06
I disabled journaling as well, but I'm finding with every reboot, I need to restart into OSX, enable journaling, and then disable it again. There has to be a better solution. Perhaps a way to disable journaling from Ubuntu?

---


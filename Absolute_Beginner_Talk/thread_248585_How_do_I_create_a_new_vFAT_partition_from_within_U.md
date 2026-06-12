---
title: "How do I create a new vFAT partition from within Ubuntu?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-09-01
I want to create a shared partition between Ubuntu and Windows, using free space in my main ext3 partition.  I think I did this with my first Ubuntu installation, but I can't remember how!

Thanks for any help you may have.

-Mark

---

### Post by ape on 2006-09-01
man mkfs.vfat

basically you want to do 'mkfs.vfat <target partition>'

---

### Post by anaconda on 2006-09-01
This lets your windows read&write to your ext3 partition..
[http://www.fs-driver.org/](http://www.fs-driver.org/)
And (ofcourse) linux can also read&write to ext3

---

### Post by mjpatey on 2006-09-01
Ape-

For some reason this brings up the manual for formatting a partition as DOS!  Very weird.

In any case, I don't want to make an entire existing partition into vFAT, just want to convert some empty space on my ext3 (Ubuntu) partition into vFAT.

Any ideas for that?

Thanks!

---

### Post by mjpatey on 2006-09-01
Anaconda, is this an experimental method, or is it safe and well-tested?

---

### Post by blent07 on 2006-09-01
I'd try a burning a LiveCD of GParted. It let's you boot right from the CD and you could resize your ext3 partition to clear up free space, make a new parition w/ that free space, and format it to FAT. Worked for me when i resized my ntfs partition. Now I've got acess to it from ubuntu and windows.

not that i really use windows much anymore...

---

### Post by galileon on 2006-09-01
the ubuntu install (or just gparted) has an option to resize the partitions, its got a little arrow. i tried that once and it worked, tho this kind of thing should only be used if you have proper backups!

---

### Post by blent07 on 2006-09-04
Definitely. I've had too many computer crashes on me, barely saved by my dad's savvy abilities. I had to back up as many files as I could, putting them on the D: drive via DOS, back with the older Windows. Of course, now they've got their "Recovery Console" (which btw, doesn't always even work! XP's got a bug in which a lot of times, the recovery console demands an administrator password which doesn't actually exist. so one has to call microsoft, get a "hotfix" patch, and that didn't even work, cuz it isn't applicable with any of the Service Packs for XP! wtf?! this all happened when i had a probelm with grub and i was trying to fixmbr via recovery, but no luck there. Thank god for ubuntu forums which was ACTUALLY helpful.)

now i'm rambling. But yeah. Lesson: back up. always.

---


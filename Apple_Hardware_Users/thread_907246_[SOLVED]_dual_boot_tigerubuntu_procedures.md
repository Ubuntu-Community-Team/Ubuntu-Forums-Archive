---
title: "[SOLVED] dual boot tiger/ubuntu procedures?"
date: 2008-09-01
forum: Apple Hardware Users
---

### Post by moore.bryan on 2008-09-01
i've looked around and can't seem to find the best way to dual-boot osx tiger and ubuntu. i've tried installing tiger first, but ubuntu's installer says the disk is "unformatted." i started by the osx disk, made two partitions (one hfs+, the other unix) and ubuntu's installer still doesn't see the disk as having any partitions. i've tried installing ubuntu first and then making a partition for tiger, but i get either an error about overlapping partitions (which there isn't; a bug is filed) or one about a partition setting that won't let me resize the ubuntu partition.

i'm at wit's end right now... could someone please point me in the right direction?

ps... i don't mind completely wiping the drive; i inherited the imac ppc from a family member.

---

### Post by tiresia on 2008-09-01
> **moore.bryan said:**
> i started by the osx disk, made two partitions (one hfs+, the other unix)
When you make two partitions with the Apple Disk Utility, leave the first one unformatted, and format the second one with HFS+
Install OSX, when you are finished, start the Ubuntu Installer and install it.
Which kind of imac is it?

---

### Post by moore.bryan on 2008-09-01
> **tiresia said:**
> When you make two partitions with the Apple Disk Utility, leave the first one unformatted, and format the second one with HFS+
Install OSX, when you are finished, start the Ubuntu Installer and install it.
Which kind of imac is it?
i tried that too, but osx disk utility won't let you leave one "unformatted." i read another post in another thread in another forum about putting osx on one partition, leaving the rest of the disk "free space," and then installing ubuntu; so, that's what i'm in the middle of now.

the imac is one of the older ppc ones.

---

### Post by tiresia on 2008-09-01
> **moore.bryan said:**
> i tried that too, but osx disk utility won't let you leave one "unformatted." i read another post in another thread in another forum about putting osx on one partition, leaving the rest of the disk "free space," and then installing ubuntu; so, that's what i'm in the middle of now.

the imac is one of the older ppc ones.

sorry, I meant 'free space'! Of course, you must start the imac from the OSX installer DVD/CD

---

### Post by moore.bryan on 2008-09-01
> **tiresia said:**
> sorry, I meant 'free space'! Of course, you must start the imac from the OSX installer DVD/CD
oh... i was confused because when i first wiped the hard drive, the osx installer gave both options--i.e., "free space" and "unformatted"--but not any longer.

everything's worked well on my latest attempt, though. i installed osx first, making two partitions with the apple disk utility (one hfs+, the other free space), and then fired-up the ubuntu livecd and installed using the guided into the largest continuous free space option. now, everything is honky-dory.

if only i could find a way to make yaboot more like grub...
;-)

---


---
title: "Burning CDs - CD-R not recognised"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by chio on 2007-02-18
Hello,

I've got a problem when trying to burn CD-Rs in Edgy. Inserting a completely blank CD-R results in it mounting as "CD-ROM Disc" on the desktop and I'm able to drag files to it. 

When I press the "write to disc" button, I'm greeted with a list of my two CD burners. Selecting the correct one (I get the same result with both) results in a message: "Please put a disc, with at least 34.2MiB free, into the drive. The following disc types are supported: CD-R, CD-RW". It does this seemingly without reading the disc to check what it is (ie. the drive doesn't light up at all, the message is immediate). 

It's odd that it seems to recognise both my burners are actually burners and not just read-only CD drives, but can't tell that a disc I've inserted is a CD-R. 

My burners as reported by Ubuntu:
- LG CD-RW CED-8083B
- CR-4804TE

If anyone needs more information, I'd be happy to provide it. 

:KS

---

### Post by chio on 2007-02-18
Interestingly, the burning works fine in K3b.

---

### Post by trtslar on 2007-05-05
i have the same problem...   anyone have an answer???

---

### Post by NT4usB on 2007-06-15
Gotta bring this one back up. I just tried to burn on both burners and get the same thing. Google tells me this is a common problem, and maybe even a bug in Feisty, but offers no solution.
I'm running Edgy. The drive works... I installed Edgy with it.
this mean anything?
ct@wimp:~$ lshal | grep volume.disc
  volume.disc.capacity = 735051776  (0x2bd00000)  (uint64)
  volume.disc.is_rewritable = false  (bool)
  volume.disc.is_appendable = false  (bool)
  volume.disc.is_blank = true  (bool)
  volume.disc.has_data = false  (bool)
  volume.disc.has_audio = false  (bool)
  volume.disc.type = 'cd_r'  (string)

---


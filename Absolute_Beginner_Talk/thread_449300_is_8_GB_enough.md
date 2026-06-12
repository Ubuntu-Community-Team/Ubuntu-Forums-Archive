---
title: "is 8 GB enough?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by sitric on 2007-05-20
hey.. is an 8 GB root and a 1GB swap partition enough for a good  performing ubuntu?

---

### Post by Outrunner on 2007-05-20
Yeah, that should be enough, but the more the merrier ehh? :)

---

### Post by jtraub on 2007-05-20
Ubuntu requires at least 4 GB for installation.

There is a tradition to make swap=2*(Amount of RAM). I think 9 GB is enough.

P.S. / + /home holds 7GB of space and everythins seems to be alright.

---

### Post by rich.bradshaw on 2007-05-20
I have a root of 4GB, no swap, and it works fine.

---

### Post by Balazs_noob on 2007-05-20
yeah it will be enough if you only store the root stuff on it ....
so no movies + music :D
mine is 5,5 GB so far and i installed everything i need :)

1 GB swap is fine too
(probably your PC won't use the swap much only if you
edit movies or large pictures :) )

---

### Post by viciouslime on 2007-05-20
> **jtraub said:**
> Ubuntu requires at least 4 GB for installation.

There is a tradition to make swap=2*(Amount of RAM). I think 9 GB is enough.

Ubuntu requires 2.5GB. That rule for swap is considered redundant these days as people now have massive amounts of memory compared to when it was useful. You should never need more than 1gb swap and even that is usually overkill.

---

### Post by Ram Crammer on 2007-05-20
I just ran  sudo du -x -c -h -s  on my machine.   It reports 4.4 G.  That's with lots of software dev tools installed.  8.5 gig with a half gig swap should get you by for quite awhile if you don't edit or store moves, or tons of music or photos.  Of course, as the disk gets toward the full side, you may experience a performance hit.  But you can get by fine for now and add a bigger disk later.  Hard disks are dirt cheap.   I picked up a used 40 Gig on Ebay for $10.  Works great!  Install the new disk, then tar everything over and reinstall Grub on the new disk.  Then you can yank out the old one, if you want to.

---

### Post by The Seeker on 2007-05-20
> **viciouslime said:**
> Ubuntu requires 2.5GB. That rule for swap is considered redundant these days as people now have massive amounts of memory compared to when it was useful. You should never need more than 1gb swap and even that is usually overkill.
Exactly.

Probably a better guideline nowadays would be twice your RAM or 512 MB, whichever comes first.

---

### Post by sitric on 2007-05-20
hey guys.. please take a look at my other problem...

[http://ubuntuforums.org/showthread.php?t=449307](http://ubuntuforums.org/showthread.php?t=449307)

---


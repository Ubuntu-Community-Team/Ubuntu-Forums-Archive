---
title: "Hard Drive Maintenance"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-08-07
In Win XP I use VoptXP to defrag and pack files on my hard drive. Is there something similar I can use to defrag and pack files on my linux  Hard Drive ?

---

### Post by Juergen on 2005-08-07
Move the files to another partition, then move them back ;-)

Linux-filesystems are all designed to
a) not fragment that badly (if you leave at least 5-10% free space)
b) suffer from fragmentation a lot less than those windows-fs

So it seems nobody sees the need to write a defragger.
There is/was an 'ext2defrag' but it's use wasn't recommended (probably because the risk of fs-corruption was bigger than any positive effects it had ;-))

---

### Post by grofaz on 2005-08-07
Cool, thanks for the answer. I think one day Linux will push Windows off a cliff. :)

Cheers!

---


---
title: "unattached inode, fsck on root filesystem!"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by bodhidharma on 2006-09-23
HEEEELLLLLPPPPPP  (please)

I helped my son build a machine this summer, we installed the
newest ubuntu on it (I'm a long-time Linux -- and Ubuntu as long
as it has existed -- user, although strangely enough I've never
had this sort of problem so I'm at a loss).  Anyway, just a few
days ago, his machine would refuse to boot (fully) ... it would
talk about some filesystem damage and go to rescue mode.  The
problem is apparently an unattahced inode in the root filesystem.
He remounts the root filesystem r/w and runs fsck, whereupon it
says running fsck on a running filesystem can cause severe
damange ... and now I'm trying to do some research on how to
help him.  Does anyone know what to do?  Or can anyone point
me to a reference work which might help out?  Thanks in advance!

---

### Post by petri on 2006-09-23
Just run ```
fsck
``` and press 'y' as an answer. **fsck** does have to complete it and for me it hasn't caused any problems. Nowadays I run ```
fsck -y
``` and then leave my pc for a while.

---

### Post by bodhidharma on 2006-09-23
So you are saying that we should just ignore the warning
about potential severe damange of fsck'ing a running filesystem?

Thanks, by the way.

---

### Post by petri on 2006-09-23
Yes, the pieces of your harddisk are **not** going to fly accross the room :)

If you have some superimportant files there please do start a LiveCD and back them up. Otherwise just ```
fsck
``` at terminal (or prompt?) and answer yes. Otherwise it won't boot.

---

### Post by McMarley on 2006-09-24
hey dad and petri
(i'm the son)

thanks for the help, I hadnt thought about asking
ubuntu forum's, basicly because I use it throught
the other computer... the one that broke down...

well now I know what to do.
thanks again

---

### Post by petri on 2006-09-24
Did it help or not? It is always good to close a thread with the result so the next person who is seeking an answer will get som advice. :)

---


---
title: "hard disk booting problem"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by sandysandy on 2007-10-12
hi! i am not able to boot from my hard disk. i am able to boot from live cd of 7.04.
kindly help.
thanx

---

### Post by taurus on 2007-10-12
Can you at least provide a little more info here?  What is the error message when you try to boot Ubuntu from your harddrive?

---

### Post by OldTimeTech on 2007-10-12
Another question is have you actually installed the live cd to your hard drive?

---

### Post by sandysandy on 2007-10-12
thanx for ur prompt reply.

i have installed the live CD to the hard disk .

on trying to boot from hard disk it says disk failure.
my system is Intel Pentium D 3.0GHz, 1 GB RAM, 2 hard disks- 160GB & 40GB.

thanx

---

### Post by OldTimeTech on 2007-10-12
Sounds like you over wrote your MBR on your first disk and now it can't find anything.

You need to use your windows disk to repair your MBR.

Next you need to make sure you've defragged the Windows side a couple of times...know how much space you've used.

At some point during the installation of Ubuntu, it will ask you about partitioning, you will need to know where your windows end and you can start your new install....also it will ask you about dual booting.

Or I guess the last question is did you install Ubuntu on the 40gb....in either case repair your MBR and then go on from there.

Anyway, I think that's your problem......and if you search in the forums...you'll find more about this which is probably better written than mine ;)

---

### Post by sandysandy on 2007-10-14
thanx.

i repaired the MBR using the windows setup CD and have got back my old win xp desktop without losing any data.

will retry with ubuntu installation for dual booting.

regards:)

---


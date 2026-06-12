---
title: "Install hangs at 23%"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2006-12-09
Hi All~
Posted about a week ago that I was having trouble installing the 64 bit version of Ubuntu.  It was hanging at 55%, no CD-ROM activity, no HDD activity.  Ciscosurfer suggested to try it a few more times or that I might have gotten a corrupt .iso.  So I tried a few more times with no luck.  
I downloaded the 32 bit version and had a couple of goes using that.  This time it hangs at 23%!  I suspected that it could be a bum HDD so I swapped it out for one that I knew works.  Still no luck.  Anyone have any input?  
Thanks for the help!!

System:
AMD X2 64
ASUS MB
80 gig Western Digital IDE HDD (Empty)
250 gig Seagate SATA (Win XP)
160 gig Western Digital SATA (intended for Ubuntu)

---

### Post by DapperMe17 on 2006-12-09
Run your install CD from a non-writing drive...such as a dvd drive, etc. Sometimes, CDRW drives have a difficult time reading the files on the disk.

Be sure that you burned(or reburn) the disk at a very low speed, to avoid writing errors.

---

### Post by steven8 on 2006-12-09
That is where mine hung up the first two times I tried it.  I burned a second disk on a CD-R, rather than a CD-RW, and tried to run from my DVD drive instead.  No go.  Same thing.  I then tried the CD-R from my read/write drive.  It installed no problem.  try a CD-R, if it was a CD-RW.

---

### Post by DapperMe17 on 2006-12-09
I've been using CD-RW media(name brand) with absolutely no problem. But, in order to run it Live, or install to HD, I must run the disk in the DVD-ROM, not the CD-RW bay. That's if you don't have a combo drive setup.

---

### Post by houstonbofh on 2006-12-09
Just to test, remove all SATA devices.  Early SATA implementation was not always completely to spec.

---

### Post by marmaladejackson on 2006-12-09
Thanks guys!
Looks like using a different CD-ROM drive worked.
Now I'm off to figure out GRUB... 
Thanks again!
-B

---


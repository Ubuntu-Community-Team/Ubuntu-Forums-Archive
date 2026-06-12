---
title: "delete /dev/hda1 to Grow /devhda3  6 hours?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by asnd16 on 2007-07-13
I am removing my NTFS partition (24.41 gig) and merging it to my linux partition?  Why does it take 6 hours???  Should I have formated the NTFS partion first? 

:confused::confused:

sux

---

### Post by Cappy on 2007-07-13
> **asnd16 said:**
> I am removing my NTFS partition (24.41 gig) and merging it to my linux partition? 

Yup .. it is probably trying to copy or move all that stuff. You should have deleted the NTFS partition and then grown the linux partition.

---

### Post by asnd16 on 2007-07-13
Dammm

---

### Post by sab0403 on 2007-07-13
Probably because the partition you're erasing was *before* the partition you're growing, and the system has to copy the entire contents of hda3 to the sectors in the beginning of hda1... so as to avoid fragmenting etc.

6 hours does sound like a bit too much, but... there's a reason behind it.

You *are* doing this from the LiveCD, right?

---

### Post by asnd16 on 2007-07-13
yes from a live cd,  I have like 4:07 hours left - I understand the purpose or why . . but then this post would have never been made I just am awed at how long this is taking . . . and bored out of my mind . . 

delete /dev/hda1 (ntfs 24.41 Gib) from /dev/hda


Then it did its thing

now its doing Grow /dev/hda3 from 87.13 GiB to 11.54 GiB

it did the copy thing but I guess it is still doing it ,. . . . copied 31.15 GiB out of the 87

---


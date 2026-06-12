---
title: "[SOLVED] hard disk association (hd0,1)"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by david2007 on 2007-09-07
I have a question , maybe its silly but i need info about this . How do i know if for example the sda5 is the hd0,0 or the hd0,1 ? I need to reconfigure the Grub menu because i installed the sabayon linux. 
Ofcourse in the beginning i lost my MBR from Ubuntu and windows ..i manage to restore it from a live cd but know i want to add the Sabayon edition in the grub menu but i dont know how to associate the hard disk name (hda4) with the letters hd0,1 . Is there a connection between them or how to i find out ? thnx:KS

---

### Post by BrendanM on 2007-09-07
hd0,1 refers to (IIRC) the second partition on the first physical drive. So hd0,0 would be the first partition on the first drive. I think that in the hda1 scheme, the letter is the physical drive and the number is the partition (which starts at 1 rather than 0).

So hda1 = hd0,0
hda2 = hd0,1
hdb1 = hd1,0

Get it?

Somebody correct me if what I said above is blatantly wrong.

---

### Post by david2007 on 2007-09-07
wow this was fast .. i will today after work  fix the new grub menu. Thnx al lot :guitar:

---


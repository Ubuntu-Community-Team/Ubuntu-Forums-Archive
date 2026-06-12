---
title: "FAT32 External USB disk SUDDENLY read-only"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by lorre on 2006-09-18
The last time (couple of hours ago) I attached my external USB disk I had no problem writing files to it. Now when I attach it, I get the error 'Filesystem is read-only' when I try to write to it.

When I type mount I can see the disk is mounted as 'rw'.

What is wrong? I have done nothing special since the last succesfull mount.

---

### Post by Jussi Kukkonen on 2006-09-18
If there are problems with mounting the disk, *mount* may try to mount the disk read-only -- try umounting and mounting the disk from the comandline  and see if there are  problems. 

VFAT has something of a reputation for being unreliable...

---

### Post by lorre on 2006-09-18
Thnx! Ejecting the disk an manually mounting it solved the problem. Only thing is; do I have to do this everytime I use my external usb disk? That would be painfull since I use the disk a lot! It used to do it alright in the beginning.

---

### Post by buffy^ on 2006-09-18
worst case, create a batch file?

---

### Post by Brunellus on 2006-09-18
> **buffy^ said:**
> worst case, create a batch file?
they're called shell scripts in *nix.

---

### Post by moore.bryan on 2006-09-18
*i had the same problem, but it self corrected after i rebooted... try that.*

---

### Post by buffy^ on 2006-09-18
> **Brunellus said:**
> they're called shell scripts in *nix.


/me adds thats to the notes.

---

### Post by Brunellus on 2006-09-18
> **buffy^ said:**
> /me adds thats to the notes.
it's a good idea, usually, to leave off suggesting solutions unless you've actually attempted them.

---

### Post by singetak on 2006-09-18
I have the same problem
But after a while i realized that the problem is from the USB
my computer is seeing it as if the lock of the usb is on
i have a sd reader also have the same problem.
So i opened it and try to fix it
the several use of this usb made it to seem lockek.

---

### Post by lorre on 2006-09-18
I've reformatted the disk to ext3 and the problem seems to be gone.

---


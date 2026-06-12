---
title: "partition disk"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by le12 on 2006-10-13
hello friends, i am an absolute beginner so correct me if i am wrong:) .I had a problem during the reseing or mount the disk(partition)(whatever you call it ).i had 29gb free so i decided to spend 15-20gb for ubuntu, however,it got an error said,"it does not got enough space for installation".yeah,i got windows xp on the same hard drive.

WHAT THE ....
any help would be appreciate!!!(please be specific)

---

### Post by ReaderRat on 2006-10-13
> **le12 said:**
> hello friends, i am an absolute beginner so correct me if i am wrong:) .I had a problem during the reseing or mount the disk(partition)(whatever you call it ).i had 29gb free so i decided to spend 15-20gb for ubuntu, however,it got an error said,"it does not got enough space for installation".yeah,i got windows xp on the same hard drive.

WHAT THE ....
any help would be appreciate!!!(please be specific)

Go to Terminal: Applications>Accessories>Terminal  and type in:```
cat /etc/fstab
``` and post what it prints out here.

---

### Post by le12 on 2006-10-13
here what it said: unionfs / unionfs vw 0 0
                   tempfs / tmp tempfs nosuid,nodev 0 0

*what is this  0 i don't know if it is a number 0 or word o ,and those things have a point in them?

---

### Post by ReaderRat on 2006-10-13
Sorry, but that looks unfamiliar to me. Someone else will have to help you.

---

### Post by raqball on 2006-10-13
If you want to use the whole 29GB of space for Ubuntu, here would be a good start for you're partitions:

hda1 swap (512mb)
hda2 / (5gb)
hda3 /home (23gb)

---

### Post by CatKiller on 2006-10-14
> **le12 said:**
> hello friends, i am an absolute beginner so correct me if i am wrong:) .I had a problem during the reseing or mount the disk(partition)(whatever you call it ).i had 29gb free so i decided to spend 15-20gb for ubuntu, however,it got an error said,"it does not got enough space for installation".yeah,i got windows xp on the same hard drive.

WHAT THE ....
any help would be appreciate!!!(please be specific)

Presumably you are still in the live cd environment, yes? I think what you've actually done is said "leave 15-20GB for XP and try and install in the rest", which the installer's complained about. Try making the resize partition number smaller and see if that helps.

Welcome to the community.

---


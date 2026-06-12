---
title: "Erase Entire Disk: use IDE1 Master (hda) or use LVM: IDE1 master?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-05-16
Lastnight I decided to stop dual booting so I reinstalled Ubuntu Dapper.

I was posed with the following two choices upon install:

1. Erase Entire Disk: IDE1 Master (hda)-40.0 GB Maxtor 9409IU8

2. Erase Entire Disk and use LVM: IDE1 Master (hda)-40.0 GB Maxtor


what does this mean and which one is the right choice. I choose option #1 btw.
:-k

---

### Post by nalmeth on 2006-05-16
You should only use LVM if you know specifically what you're doing.
Otherwise, I think you picked wisely

---

### Post by RAV TUX on 2006-05-16
[QUOTE=nalmeth]You should only use LVM if you know specifically what you're doing.
Otherwise, I think you picked wisely[/QUOTE]

Thanks. I was slightly concerned.

---

### Post by MediaHound on 2006-06-24
What's the difference?

---

### Post by dmizer on 2006-06-24
[QUOTE=MediaHound]What's the difference?[/QUOTE]
for one, lvm allows you to use a huge drive 100+ gig on a system which the bios does not support such a large disc.  but the ext3 option (option 1) does not.

also with lvm, you can adjust the home partition size on the fly for systems who have multiple user accounts.  for most users, this arrangement is not necessary.

---

### Post by MediaHound on 2006-06-24
Tq!

---

### Post by wietse on 2006-07-11
just the info I needed, thanks!

---


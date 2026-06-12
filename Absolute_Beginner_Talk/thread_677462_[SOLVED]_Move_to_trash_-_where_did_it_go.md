---
title: "[SOLVED] Move to trash - where did it go ?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by jryprt on 2008-01-24
I was looking at a windows file (windows side)thur ububto 7.10 and hit Move to Trash but it did not go in the Trash where did it go? I would like it back.

---

### Post by wolfen69 on 2008-01-24
open your home directory and choose >view>show hidden files. look for .trash and see if it is there.

---

### Post by jryprt on 2008-01-24
> **wolfen69 said:**
> open your home directory and choose >view>show hidden files. look for .trash and see if it is there.

Its empty

---

### Post by LaRoza on 2008-01-24
If it was on a different drive, it will be in .trash-username

---

### Post by jryprt on 2008-01-24
> **LaRoza said:**
> If it was on a different drive, it will be in .trash-username

Its was on the windows partitions I was looking at it thur ubuntu & hit Move to Trash.

---

### Post by blueridgedog on 2008-01-24
I suspect on the windows drive you refer to is a folder called .Trash-USER (where user is your user account) and your file is in there.

So, if the drive is mounted via /media/sda1, the folder would be 

/media/sda1/.Trash-USER

You can see hidden folders in nautilus with CTR+h.

---

### Post by jryprt on 2008-01-24
> **blueridgedog said:**
> I suspect on the windows drive you refer to is a folder called .Trash-USER (where user is your user account) and your file is in there.

So, if the drive is mounted via /media/sda1, the folder would be 

/media/sda1/.Trash-USER

You can see hidden folders in nautilus with CTR+h.

Thank you that it got it back.

---


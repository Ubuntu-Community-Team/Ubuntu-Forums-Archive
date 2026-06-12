---
title: "Partition trouble"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by Porta on 2006-06-24
I have a vfat partition on a second harddrive wich i cannot work with in a normal way.
It's impossible to change the permision on the files stored there.
I've created a mount-point, edited fstab using the information from psychocat but it didn't help.
For example if i want to change a file, or work with a file in openoffice it is read-only and i can't change a thing.

Is there something that can be done about this?

regards

---

### Post by muep on 2006-06-24
I'm not sure, but does setting

umask=0000

in the fstab options help?

---

### Post by Porta on 2006-06-24
Well, it's worth a try, i will see what happens.

regards

---

### Post by Porta on 2006-06-24
That did the trick, thanks for the assistance.


regards
Porta

---


---
title: "mounting"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by greg m on 2006-07-26
i cant get my 3.5 flopt to mount, sometimes my zip100 will. i have not tried the ls 120 . this is my old winpos 98 and i did not take anything out of it.

thank you  greg

---

### Post by OU812 on 2006-07-27
I am running a freshly installed kubuntu and I just noticed that my floppy is not listed in my fstab. Take a look at yours. You should have an entry that looks something like this

dev/fd0         /mnt/floppy      auto        noauto,user      0   0

If not, from a terminal do

sudo gedit /etc/fstab

and insert this line. Then from the terminal do

sudo mkdir /mnt/floppy

john

---


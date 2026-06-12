---
title: "Hard drive partition issues. help please!"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by isotope_239 on 2007-12-03
Aryt, here's the thing, I can read and write data to all of the other partitions (that includes ntfs windows file system) in my hard drive. the thing is, i can't write data on the partition where ubuntu is actually installed. I tried altering the permissions, but still nothing happened IE "you are not privileged to change permissions. is this something normal? Sorry i've been only using ubuntu for 2-3 weeks an it takes some time to learn it I guess.. :(. thanks in advance!

---

### Post by jken146 on 2007-12-03
You have permissions to write to everything in the directory /home/<your-user-name>.  If you want to write to files outside of that directory, you must do so as root, i.e. with the sudo command (and with care!).  This doesn't apply to NTFS partitions.

---

### Post by jken146 on 2007-12-03
Here's a good page for newbies about file permissions: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by isotope_239 on 2007-12-15
Got it! Thanks man. :)

---


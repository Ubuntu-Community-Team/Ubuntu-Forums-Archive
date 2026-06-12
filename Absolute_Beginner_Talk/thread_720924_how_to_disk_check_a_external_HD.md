---
title: "how to disk check a external HD"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by nynoah on 2008-03-10
I have mounted my external HD way over 30 times.  I want to do a force check on it.  How would I go about doing that just on my external hard drive?

Thanks

---

### Post by logos34 on 2008-03-10
sudo umount /media/sdbx (or whatever the ext drive partition is)

sudo fsck /dev/sdbx

---

### Post by nynoah on 2008-03-10
Thanks I will try that.

Noah

---

### Post by nynoah on 2008-03-10
Ohhh forgot to ask.......how do I determine what drive this is?  Its there a command to tell me?

---

### Post by nynoah on 2008-03-10
Ok just figured out a round about way to check that.  I opened up Gparted and looked that way.

---


---
title: "System&gt;Disk?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by tordan on 2006-12-28
Im a 6.10 edgy user and threads keep telling me to go to System>Disks to mount a second hardrive that I have already partitioned. However, I go to System and there is no "disk" or in any of the subfolders. Why don't I have a "disk" option? New and lost...

---

### Post by bruenig on 2006-12-28
Ubuntu Dapper, version 6.06 had a system>disk but edgy 6.10 does not, so those threads were probably created during dapper's reign.

---

### Post by tordan on 2006-12-28
What do I do then? Another program?

---

### Post by bruenig on 2006-12-28
Well I am not a big gui guy myself, if you want to mount a disc, you can just do
```
sudo mount /dev/whatever /mount/point
```
if that helps. I am not sure if another program replaced the system>disks perhaps someone else who reads this thread know.

---

### Post by tordan on 2006-12-28
Thanks for the response.
what information would replace "whatever" and how do I specify which drive partition to mount?

---

### Post by bruenig on 2006-12-31
> **tordan said:**
> Thanks for the response.
what information would replace "whatever" and how do I specify which drive partition to mount?

Do the following to determine what the partition's "whatever" is
```
sudo fdisk -l
```

---

### Post by Bartender on 2006-12-31
tordan -
I'd suggest printing the output of fdisk -l and putting it in a notebook.  It's good to have that info close to hand.

---


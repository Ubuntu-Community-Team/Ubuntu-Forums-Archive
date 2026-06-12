---
title: "Old windows partition didnt go away..."
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by triskit on 2008-02-08
When I installed ubuntu I selected the option (cant remember the exact words) to partition the hard drive exclusively to ubuntu... at least i thought thats what I did... I seem to be missing 30 GB (about the size of my windows files). Is there a way to get that space over to ubuntu with a new partition or something? 

Id rather not have to reinstall Ubuntu, as Ive just gotten it pretty much how  like it w/ new programs, etc.

This is actually my roommates laptop, so there is a chance that I'm just wrong about there having been more space on it. Is there an easy way for me to check for stuff on the drive outside of the Ubuntu partition?

Thanks

---

### Post by Desperate on 2008-02-08
I would see with Gparted what is there and what it is. If it still doesn't show your 30 gig then open a terminal and type sudo fdisk -l that should show everything on your hard disk(s)

---

### Post by triskit on 2008-02-08
Thanks a lot
 
apparently the disk is just smaller than we remembered.

---

### Post by antisocialist on 2008-02-08
there is also the fact that manufacturer's say a hard drive is for example 320GB, meaning 320 billion bytes, not actual 320GB of storage, and after the conversion you end up with a 299GB hard drive. i dont know for sure if this is your problem, but it could be.
EDIT: oh or it could be that you installed about 30GB of stuff o.O

---

### Post by jw5801 on 2008-02-08
If you're curious this is because 1GB according to a hard drive manufacturer is 1,000,000,000B. The problem with this is that data works in base 2 so 1kB is actually 1024 (2^10) bytes, 1MB is 1024kB etc etc.

---


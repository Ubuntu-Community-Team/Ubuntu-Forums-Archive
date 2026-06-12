---
title: "How does installing 6.06 over 5.10 not affect the /home partition?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-07-12
If you had breezy, and you had seperate / and /home partitions, I've heard that you could do a fresh install of dapper over breezy, but that it wouldn't touch your /home partition, only your / partition.  

But how can that be true?  In the install it tells you where to assign mount points, don't you have to tell it that your /home is already there and you don't want to destroy it?  I don't think that's an option in gparted.

---

### Post by Titus A Duxass on 2006-07-12
During the install, you can click on your existing /home and instruct the process not to reformat the partition.

---

### Post by user1397 on 2006-07-12
> **Titus A Duxass said:**
> During the install, you can click on your existing /home and instruct the process not to reformat the partition.AH!!!
i did not know that...:-k

---

### Post by Titus A Duxass on 2006-07-12
You do now!

That's the thing with linux, there's always something to learn!

If you do this just make sure that you tell the system not to reformat your /home and of course before you start back up /home.

You will also need to save things like Bookmarks and address books as they can sometimes disappear.

I've had a separate /home for years.  The advantage is that you can change distro without having to worry.

You can even move /home to another computer.

---


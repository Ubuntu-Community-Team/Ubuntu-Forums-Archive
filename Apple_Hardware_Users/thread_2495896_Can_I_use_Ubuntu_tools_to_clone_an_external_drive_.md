---
title: "Can I use Ubuntu tools to clone an external drive that contains MACOS (High Sierra)?"
date: 2024-03-06
forum: Apple Hardware Users
---

### Post by wb0gaz on 2024-03-06
(moderators - if this posting is not in the correct section or is otherwise not usable, please assist/advise)

I wish to clone (onto a larger device) the startup drive removed from a MAC OS system (High Sierra) which contains Apple's HFS+ filesystems.

I tried dd to duplicate the drive's contents onto another one, then gparted to relocate the third (small, "recovery") partition to the end of the larger drive, however, gparted does not appear to have HFS+ filesystem support (needed to expand the second/root filesystem to take up the available space between end of the existing root/main filesystem and start of the newly relocated third/recovery filesystem).

Can this task be done with command-line (or GUI) tools available in the Ubuntu/Linux environment?

I do not wish to use a commercial product for this (one-time) task.

Thank you, and happy to provide any needed clarifying information.

---

### Post by TheFu on 2024-03-06
dd, ddrescue, cat, cp and 50 others can all clone a disk.  After that, it is up to you to deal with the foreign file system and whatever partitioning is needed due to that foreign file system.

With many Unix file systems, we cannot just move a partition and add other partitions and expect it to work.  This is a MacOS question, not Ubuntu.  At a minimum, it belongs in the MacOS sub-forum here, but really needs to be asked on a Mac-specific forum, I'd bet.

BTW, any MacOS in the last 20 yrs would have the same capabilities to clone the disk (they have root/sudo and cp, right?), since it is based on Unix.

---

### Post by wb0gaz on 2024-03-06
Thank you TheFu for the reply. I had tried on the official apple community but that yielded only a commercial product. I'll look for the macos sub-forum on ubuntu forums (overlooked when I made this post) and see if there's any similar discussion there.

---

### Post by gezzer2 on 2024-03-06
clonezilla supports HFS+ along with many other file systems and i believe is available from the Ubuntu repros ..

[https://clonezilla.org](https://clonezilla.org)

---

### Post by oldfred on 2024-03-06
Moved to Apple users sub-forum.

---


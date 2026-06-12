---
title: "Working with the file system (including taking back the space used by Windows)"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by 0MG on 2006-07-12
When I originally set this laptop up, I was using a beta version of Vista. That was the first install. I installed Dapper on top of it. 

Now I want to take back the space previously used by Vista.

I have formatted the old NTFS partition, but I am unsure how to utilize that space. What I would like to do is set it up as /home. How can I do that without wiping out my current /home?

TIA.

---

### Post by professor_chaos on 2006-07-12
I would suggest you use the program gparted. It should already be installed in dapper. Providing you /home is already a seperate partition, you can just resize that partition to include this new space. First, you need to delete that old NTFS partition and then resize. 

WARNING: partitioning/resizing/moving partitions is not the safest thing, so backup any files you really don't want to lose.

---

### Post by 0MG on 2006-07-12
Thanks for the reply.

I messed up when I installed dapper and the partitioning is as vanilla as possible. Vista was hda1, and dapper was all on hda2. I guess that's where my problem lies. Will I need to back up /home completely and then set hda1 as /home, then copy the backed up /home to its new 'home'?

---

### Post by catlett on 2006-07-12
Aysiu has another great how to that deals with this issue
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---


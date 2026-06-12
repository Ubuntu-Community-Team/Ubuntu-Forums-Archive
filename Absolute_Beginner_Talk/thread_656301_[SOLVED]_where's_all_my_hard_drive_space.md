---
title: "[SOLVED] where's all my hard drive space?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Meph1st0 on 2008-01-02
I installed a spare 40 GB hard drive in my server.  I used GParted to create a single primary partition using the ext3 filesystem mounted at /media/Music

In Gparted it says I have a approximately 40 GB free, but the folder properties in /media/Music says there's only 23 GB free.  Where's the other 17 GB?  Mind you, the folder is empty.

---

### Post by tech9 on 2008-01-02
this sounds strange...

maybe try deleting the partition and creating it again, but mount it as something different, like /home/music

---

### Post by icheyne on 2008-01-02
[Disk usage analysis and cleanup tools]("http://www.linux.com/articles/51600")

---

### Post by Meph1st0 on 2008-01-02
Oops.  It wasn't mounted at all.  I thought it was but I guess it wasn't.  That's 23 GB was how much is left of my root partition.  sorry. :)

---

### Post by tech9 on 2008-01-02
> **Meph1st0 said:**
> Oops.  It wasn't mounted at all.  I thought it was but I guess it wasn't.  That's 23 GB was how much is left of my root partition.  sorry. :)

That's ok ...
It would be incredibly strange if your drive was mounted and only showed 60% of your HD

---


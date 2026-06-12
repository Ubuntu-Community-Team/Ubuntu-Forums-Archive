---
title: "Grub Error 15?  Root gone?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by learning on 2006-05-19
Here is my problem...

I partioned my hard drive (Have Win XP) and created 2 partitions for ext 3 and swap for unbuntu and tried to install dapper from live cd... It wouldn't work.  Would start configuring HD from partition manager and quit.

I didn't have this trouble with Breezy so I installed Breezy from disc and everything worked fine.  Grub would come up and let me pick windows or Breezy.

So, then I tried to install Dapper again.  Went through partitioner... it started formatting and quit again.  Now, it won't boot at all.  I get Grub loading then error 15.

I decided to call it quits with dapper and just re-install Breezy.  BUT when I go through partitioner, all the settings are there.  I tell it to go ahead but when it starts it say error:  no root partition.  

What do I do?  Did I mess up bad?

---

### Post by joshrobinson on 2006-05-19
[QUOTE=learning]Here is my problem...

I partioned my hard drive (Have Win XP) and created 2 partitions for ext 3 and swap for unbuntu and tried to install dapper from live cd... It wouldn't work.  Would start configuring HD from partition manager and quit.

I didn't have this trouble with Breezy so I installed Breezy from disc and everything worked fine.  Grub would come up and let me pick windows or Breezy.

So, then I tried to install Dapper again.  Went through partitioner... it started formatting and quit again.  Now, it won't boot at all.  I get Grub loading then error 15.

I decided to call it quits with dapper and just re-install Breezy.  BUT when I go through partitioner, all the settings are there.  I tell it to go ahead but when it starts it say error:  no root partition.  

What do I do?  Did I mess up bad?[/QUOTE]

when in the paritioner, select the partition you want to be the root parition and make sure its mount point is /

if you want to try again with dapper, delete all the paritions that you dont need, and tell it to automatically parition the free space

---

### Post by learning on 2006-05-19
That got it going again!  Re-installing now.

Thank you!

---

### Post by joshrobinson on 2006-05-19
[QUOTE=learning]That got it going again!  Re-installing now.

Thank you![/QUOTE]

your welcome :D

---


---
title: "[SOLVED] enabling read&amp;amp;write in filesystem ?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by robb234 on 2007-07-13
hi everyone,
i need some help here

currently my filesystem drive is "read-only",
i wish to change it to "read and write" so that i can save files onto that drive...
i've tried before, changing it from properties, but it doesn't work,
it says "u dont have the permission"
so is there any way to make it "read n write"  ?
thanx in advance  :)

PS : i have used NTFS Configuration Tool to enable "read-write" on my C: and D: 
(which is Win XP, i run a dual-boot system)
but the tool doesn't affect filesystem....

---

### Post by felicity on 2007-07-13
I use: 
```

sudo chmod -R a+rwx /media/storage

```
but change /media/storage to wherever your drive is mounted.

---

### Post by petedct on 2007-07-13
By "filesystem drive" I think you mean the top level of the root partition. I don't think storing data there is recommended . That's where Ubuntu and all of your applications are installed. If something goes wrong I'd imagine you'd really have problems. You probably want to consider staying with your /home partition or you may want to consider creating a new partition.

---

### Post by robb234 on 2007-07-15
well if that's the case, i guess i need new partition then :)

thx alot everyone

---


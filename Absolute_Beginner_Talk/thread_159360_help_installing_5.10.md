---
title: "help installing 5.10"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by kufio on 2006-04-12
I have my hard disk partitioned in three: c:\ with 100 mb where I only keep the boot.ini and ntldr for my win xp 
on the next partition(hda5) I tried to install  ubuntu 5.10 and on (hda6)E:\ I have the xp
I wanted to install 1 GB swap partition mounted on /  and a 15 GB ext3 partition l mounted on /, do I have to mount both the swap and ext3 
part on / ?
I tried this way but it gives me an error. I need some suggestion
Thanks

Edit: Do they have to be primary or logical partitions?

---

### Post by taurus on 2006-04-12
Swap partition will be mount as swap, NOT part of /.  In fact, it has an ID of 82 where Linux has an ID of 83.  When you get to the partitioner, if you tell it the partition is swap, it will take care of itself so you don't have to worry about where to mount it...

---

### Post by Sef on 2006-04-13
> I wanted to install a 100mb swap partition 

How much memory do you have?   That's an awfully small swap unless you have a lot of ram like a gb, then you really don't need it.

---

### Post by kufio on 2006-04-13
[QUOTE=Sef]How much memory do you have?   That's an awfully small swap unless you have a lot of ram like a gb, then you really don't need it.[/QUOTE]
Sorry, i meant 1gb

---

### Post by kufio on 2006-04-13
[QUOTE=taurus]Swap partition will be mount as swap, NOT part of /.  In fact, it has an ID of 82 where Linux has an ID of 83.  When you get to the partitioner, if you tell it the partition is swap, it will take care of itself so you don't have to worry about where to mount it...[/QUOTE]
Do I have to make the partitions logical or primary?
Thanks

---

### Post by Sef on 2006-04-13
> Sorry, i meant 1gb

You really don't need a swap then, unless you are doing something very memory intensive.

---


---
title: "Help, install on new hard drive"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Uncle Che on 2007-01-03
I just put in a fresh brand new hard drive in my laptop. 

1) The BIOS recognizes it. 

I want this to be dual boot (for work) so I tried to install Windows first and it failed at the partition manager step. I thought oh well, maybe I need to partition it first.(?) so I put in my Ubuntu. The Gnome partition manager doesn't recognize the disk as present and I ran sudo fdisk -l and nothing showed either. 

Any ideas? What steps am I forgetting to do?

---

### Post by Frak on 2007-01-03
**When you install Windows, let it go to terminal and enter these commands.**

```
1. D:\ (this will change drives to your CD drive)
2. cd WinNT
3. Format (and then whichever drive you want to format i.e C:\ on mine, depends on yours)
4. oemsetup
```

Just remember, on step 3, the drive HAS TO BE IN CAPS!, or it will say "cannot find drive", it is case sensitive just like Linux is, in this state.

Hope that works.

---

### Post by Uncle Che on 2007-01-03
I tried every jumper configuration available and still no luck. The BIOS recognizes the drive but Ubuntu doesn't and neither does Windows for installing so I put the drive in an external case to partition it. Again, Ubuntu didn't recognize it. Windows did and partitioned it, but when I put it in my laptop to boot up, it wouldn't install Windows or Ubuntu. Why? It didn't recognize it. In the case, the partitions are viewable in Windows but not viewable in Ubuntu, in fact, in Ubuntu, the drive makes clicking sounds. 

I assume I have a bad hard drive so will take it back to the shop.

---

### Post by Frak on 2007-01-03
Probably a good idea, I mean Ubuntu does have problems with Hard Drives that are cased, but it shouldn't mess up the drive just trying to find it, try a new one, and may I ask, what brand was it?

---


---
title: "creating a partition to install Windows XP"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by anarchoi on 2007-04-13
hi,

my PC currently only have linux ubuntu on it

how can i create a partition that will allow me to install windows xp on it?

---

### Post by Seisen on 2007-04-13
You best best is to download the gparted live-cd and burn that. Gparted will help you partition your harddrive. 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=500778]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=500778")

---

### Post by anarchoi on 2007-04-13
is there a step-by-step tutorial on how to make a partition for windows xp?

i'm a real big newbie

---

### Post by bcmiller on 2007-04-13
> **anarchoi said:**
> is there a step-by-step tutorial on how to make a partition for windows xp?

i'm a real big newbie


You just have to go into the live cd and run GParted.  You then select the large partition and resize it.  Reduce the size after the partition by 10 to 15 gigs and then save the changes.  I will then list the space as unallocated.

From there you can run your XP install CD and it should detect the unallocated space.  

The problem you will have is that XP doesn't like being the second OS installed.  At the very least you will have to reinstall grub when all is said and done.

The preferred method is to install XP first and then install Ubuntu to dual boot.  That's not practical if your Ubuntu is setup the way you want it I know... Im dealing with the same issue my Windows ME cd failed to format the unallocated space for some reason (I have to upgrade from ME to XP)

What I ended up doing is installing VirtualBox and running XP as a virtual OS.  If you want to play games this is no solution.

---


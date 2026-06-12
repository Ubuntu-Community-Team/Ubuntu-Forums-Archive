---
title: "[SOLVED] how to reinstall ubuntu"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by cragger on 2008-01-27
ya so Ubuntu crashed and will not load on my dual boot vista and ubuntu, vista works fine, i just need to reinstall ubuntu without hurting poor fragile vista

---

### Post by Majorix on 2008-01-27
Download the GParted LiveCD. Use it to delete all partitions related to Ubuntu. Then pop in the Ubuntu disk, and on the partitioning screen choose "use the largest continuous free space" or whatever that is called.

---

### Post by maybeway36 on 2008-01-27
Should be easy. If you don't need to back up, just reinstall, using the old root as root but checking the "format" box.

---

### Post by Kilz on 2008-01-27
> **cragger said:**
> ya so Ubuntu crashed and will not load on my dual boot vista and ubuntu, vista works fine, i just need to reinstall ubuntu without hurting poor fragile vista

Place the install disk in the drive, reboot and reinstall.

---

### Post by cragger on 2008-01-27
> **Kilz said:**
> Place the install disk in the drive, reboot and reinstall.

just reinstall over the ubuntu partition, wont that make like double swap partitions as it wont delete the old one?

---

### Post by Majorix on 2008-01-27
> **maybeway36 said:**
> Should be easy. If you don't need to back up, just reinstall, using the old root as root but checking the "format" box.

Do it this way if you have a separate /home partition. Not absolutely necessary but makes it easier.

---

### Post by cragger on 2008-01-27
ok sorry im a little confused, what exactly do i do,... i dont need to back up ubuntu, i just want it in the exact same place but i want it to work

---

### Post by Majorix on 2008-01-27
Just follow my post then ;)

---

### Post by cragger on 2008-01-27
which one, just wrighting over the ubuntu partition, or erasing it with GParted and reinstall

---

### Post by Majorix on 2008-01-28
The GParted option. Sorry for the late reply though.

---

### Post by LeAstrale on 2008-01-28
i would go for the GParted way also. even though i have had no luck with my Dual boot with Vista.. however that isn't really a problem to me since im not a "vista" man, i definately prefer xp (when you have to choose a windows OS that is)

---

### Post by cragger on 2008-01-28
eh no problem, i will go witht the gparted and let you know how it went, 
o and with windows, i would go with xp for stability and vista just kinda sucks, i just have a bunch of windows stuff that i still need to use still, so hence the dual boot

---

### Post by cragger on 2008-01-28
> **astral-1 said:**
> i would go for the GParted way also. even though i have had no luck with my Dual boot with Vista.. however that isn't really a problem to me since im not a "vista" man, i definately prefer xp (when you have to choose a windows OS that is)


y didnt our vista dual boot work, mine works fine, (well untill i messed up ubuntu)


o and before i forget thanks allot for everyones help

---

### Post by LeAstrale on 2008-01-29
Your welcome cragger..

---

### Post by cragger on 2008-02-06
dont no if anyone will reply but finally found time to do al of this and do i want the live cd of g parted, and what do i need to change with the program

---

### Post by ugm6hr on 2008-02-06
> **cragger said:**
> dont no if anyone will reply but finally found time to do al of this and do i want the live cd of g parted, and what do i need to change with the program

Easiest way...

Use Ubuntu LiveCD.
Once booted, go to System-> Administration-> Partition Editor (GParted)
**Identify the Ubuntu partition and Swap partition** (i.e. make sure you don't choose Vista!)
Right-click on the 2 partitions identified and ensure unmounted, then delete.
Click Apply.

Once it has done this....

Double-click the install icon on desktop (still in LiveCD).
As previously suggested - Use **Guided - Largest Free space** option (note default option is not this one)
Go through the other options as previosuly.

When done, it should offer to reboot.
It should then just work (in theory).

---

### Post by cragger on 2008-02-06
will this delete the partition or the data on it?

---

### Post by cragger on 2008-02-06
nvm ya ive figured it out, and accidentally i compressed the recovery partition so it will be another 30 mins, just waiten now

---

### Post by cragger on 2008-02-07
hah yes it works, my ubuntu is up and running now, thank you

---

### Post by ugm6hr on 2008-02-07
> **cragger said:**
> hah yes it works, my ubuntu is up and running now, thank you

Welcome back :)

---


---
title: "Error!!"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by angel_zone on 2008-03-24
i'm trying to install ubuntu 7.10 on my pc every thing was just fine till the partitioning step i did it as followin; exe3 / 30000 MB , swap 900 MB and exe3 /boot 560 MB the remaining free space then clicked forward but i received this message {ERROR WINDOWSSYSTEM32CONFIGSYSTEM.LOG is 1K but it has 2 clusters 16K} i click ignore but the same message appears again but with 5 cluster 40K(what is it anyway??!!) i ignored this too then i received another one an so on till finally this appears {FATAL ERRO; BAD FAT:unterminated chain for RECYCLEDDESKTOP.INI. you should run dosfscn or scandisk} i clicked o.k then it asks me to go back the partitioning menu and correct errors?????:( sorry for the long post but i write the messages as it appears this is the second time i quit the live CD and booted to windows xp,checked the disks and there were not any errors?? can any body help me in this:confused:

---

### Post by angel_zone on 2008-03-24
hey gus somebody please tell me what to do? should i ignore this and move on within the installation process?

---

### Post by angel_zone on 2008-03-24
????????????????????????????

---

### Post by Darganot on 2008-03-24
are you wiping out xp???

---

### Post by Darganot on 2008-03-24
you could try running gParted first (it's in system -> administration -> gParted or Partition Manager) and make sure the drive is wiped clean before you start the installation, that there's nothing on the drive.

---

### Post by Locutus_of_Borg on 2008-03-24
run check disk on your windows partition

if you're resizing it, it may lead to errors in the installation if theres something askew with windows

---

### Post by angel_zone on 2008-03-24
> **Darganot said:**
> you could try running gParted first (it's in system -> administration -> gParted or Partition Manager) and make sure the drive is wiped clean before you start the installation, that there's nothing on the drive.

i already done this in widows and every thing was o.k i would ignore all of this but the message of fatal error made me worry:confused:

---

### Post by angel_zone on 2008-03-24
> **Locutus_of_Borg said:**
> run check disk on your windows partition

if you're resizing it, it may lead to errors in the installation if theres something askew with windows

i did not resizing windows i just used the free space after deleting one of mt FAT32 partitions for ubuntu and what is the cluster thing by the way:)

---

### Post by Locutus_of_Borg on 2008-03-24
ive never heard of the clusters thing, and i cant see a reason why anything windows would crop up in a linux install on a entirely separate partition

i just recall running into problems trying to shrink my windows install down too far that sounded familiar

---

### Post by Darganot on 2008-03-24
> **angel_zone said:**
> i already done this in widows and every thing was o.k i would ignore all of this but the message of fatal error made me worry:confused:

You can't do that in windoze it must be done from the live CD...make sure you're ready to get rid of all that data too.

---

### Post by Darganot on 2008-03-24
> **angel_zone said:**
> i did not resizing windows i just used the free space after deleting one of mt FAT32 partitions for ubuntu and what is the cluster thing by the way:)

Wait a second did you delete a partition windows was using?  Yes that will cause errors as it doesn't see the data there.  Are you trying to set up a dual boot system or to just wipe the drive?

---

### Post by angel_zone on 2008-03-24
i'm thinking doing something.. create the ubuntu partitions using my disk manger or magic partition then retry installing from the CD how do you find that guyes ?should i go on

---

### Post by angel_zone on 2008-03-24
> **Darganot said:**
> Wait a second did you delete a partition windows was using?  Yes that will cause errors as it doesn't see the data there.  Are you trying to set up a dual boot system or to just wipe the drive?

the partition i deleted was totally empty i already did that once i had ubuntu installed on my old hard drive and every thing was fine but i had to buy another one so i/m re-installing it and yes i want to set up dual boot i can't get rid of windows right now

---

### Post by angel_zone on 2008-03-24
o.k can i resize windows partition usin partition magic Gparted live ce?
and how can i do that any guides please?

---


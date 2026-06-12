---
title: "evil windows-something i got told"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by yatesDELTA on 2006-03-08
i heard somewhere that when i get around to reinstalling windows on its HDD it will destroy linux as it was there first

is bill gates that evil!?!?!?

---

### Post by meborc on 2006-03-08
i think the problem is more that your boot menu will be overwritten and you can't boot to your linux sys...

if you previously have win in a separate partition, then installing a new win there souldn't (DON'T TAKE MY WORD FOR IT) touch your linux partitions... BUT it will delete grub/lilo (I THINK) or i got it all wrong :mrgreen:

---

### Post by yatesDELTA on 2006-03-08
i had them on seperate HDD's

---

### Post by meborc on 2006-03-08
i have never encountered anyone who does linux -> windows leap... :D usually it is the other way round...

---

### Post by yatesDELTA on 2006-03-08
its becasue i got a virus on windows and i have a copied disk which is not working and someone told me that gates is so stupid he will ruin my computor if it means i use winsows

---

### Post by LordBug on 2006-03-08
Windows won't overwrite any partitions unless you explicitly tell it to.  It doesn't seek out other OS's and destroy them.  You tell it which partition to use, and it'll ignore the rest.

It will re-write the MBR of the first drive on your system (whether or not this is the Windows drive), which can overwrite your GRUB installation.  You can change this back with a LiveCD easily enough.

---

### Post by yatesDELTA on 2006-03-08
oh okay then

---

### Post by Lord Illidan on 2006-03-08
With my machine, an installation of Windows XP wouldn't continue until I wiped the first partition of the master drive, which was a Linux root partition. Luckily, my /home partition remained intact. But I stopped using XP and switched to Ubuntu again, I hated XP after Ubuntu.

---


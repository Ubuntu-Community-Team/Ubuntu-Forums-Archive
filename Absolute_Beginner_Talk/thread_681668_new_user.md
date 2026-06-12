---
title: "new user"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by sidymani on 2008-01-29
now i am running windows xp, service pack 2 on my laptop. my computer has three partitions on the hard drive. i want to switch to ubuntu 7.10 but i am afraid of few things. last time i installed red hat linux on my computer, it formatted my all computer and my all data was lost. this time i have a lots of data and i don't want to loose them. plz tell me if it is possible to install it on one partition of my hard drive after removing windows xp. i don't want to keep two OS. 

the next thing i am afraid of is if it will fit my screen resolution 1280x800 (wide screen).

i have English US + german keyboard installed......is it possible that i can use English + german keyboard  on ubuntu also.

thanks for your help

---

### Post by drowner on 2008-01-29
Screen will be no problem

Keyboard will be no problem

If the data that you wish to keep is on the same drive as XP, then you can't install ubuntu over the top or it will format the entire partition.

Do you have an external drive you could back the data up to?

---

### Post by dward526 on 2008-01-29
If you watch your installation setings to target an unused partition, you should have no problem with your install.  You should always back up important data first however.

---

### Post by emarkd on 2008-01-29
Always back up.  Things go wrong.  Computers crash.  People accidentally hit the wrong buttons.  Always back up.

That being said, Ubuntu's installer can handle your partitioning needs and will leave the rest of your disk alone if you tell it to.

---

### Post by sidymani on 2008-01-29
thanks for your help
no i have all the data in two other partitions........so it means i can safely install ubuntu 7.10 in the partition in which i have xp now without any loss. 
no i don't have any unused partition.

---

### Post by mgm2rr on 2008-01-29
If you think you may want to use XP in the future I would recommend just shrinking XP's partition using Gparted off of a live CD, and then adding Ubuntu to a new partition in the extra space.  Its much easier for a new user to install Ubuntu onto a system that has XP on it and then do a dual boot than it is to reinstall XP on a system that already has Ubuntu.

---

### Post by forrestcupp on 2008-01-29
> **sidymani said:**
> thanks for your help
no i have all the data in two other partitions........so it means i can safely install ubuntu 7.10 in the partition in which i have xp now without any loss. 
no i don't have any unused partition.

Yes.  The latest Ubuntu can read and write to NTFS partitions by default.  So you will be able to access the data if it is on a different hard drive.  I will warn you, though, that Linux support for NTFS is a lot slower than the native ext3 file system, it's also slower than reading and writing to NTFS in Windows.  So you may want to transfer your data and format those drives to ext3, then move your data back.

---


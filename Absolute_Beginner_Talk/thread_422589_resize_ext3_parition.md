---
title: "resize ext3 parition"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-04-25
i want to create a new partition on my hdd. 
its currently setup as 1 ext3 partition and a swap partition.

i tried booting into the live CD and running gparted, but it would not let me resize this partition, only format..

is there any way i can shrink my current ext3 and then create a new one? (so i can have my /home and mp3s on a seperate partition)


thanks.

---

### Post by deathbyswiftwind on 2007-04-25
I dont know but have you tried installing gparted and seeing what options it gives you?

---

### Post by Sef on 2007-04-25
Get the [GParted]("http://gparted.sourceforge.net") LIve CD.  It is more up-to-date than the Ubuntu Live CD.

---

### Post by az on 2007-04-25
> **PetePete said:**
> i want to create a new partition on my hdd. 
its currently setup as 1 ext3 partition and a swap partition.

i tried booting into the live CD and running gparted, but it would not let me resize this partition, only format..

is there any way i can shrink my current ext3 and then create a new one? (so i can have my /home and mp3s on a seperate partition)


thanks.

Ubuntu uses your swap, when you boot the live cd.  You need to unmount your swap.  The you will be able to partition your disk.

---

### Post by PetePete on 2007-04-25
thanks will do.

but can someone confirm to me that it is possible to resize an ext3 partition?

current setup is something like 
0-59gb = ext3, 59-10gb = swap

---

### Post by PetePete on 2007-04-25
> **az said:**
> Ubuntu uses your swap, when you boot the live cd.  You need to unmount your swap.  The you will be able to partition your disk.


thanks for that. i'll try

---

### Post by az on 2007-04-25
> **PetePete said:**
> thanks will do.

but can someone confirm to me that it is possible to resize an ext3 partition?

current setup is something like 
0-59gb = ext3, 59-10gb = swap

Yup.

---


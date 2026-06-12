---
title: "logical partitions"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Staraloppan on 2007-02-04
My HD is allredy in 3 main partitions, now i need to make 2 logical partitions can anyone help me?:) :) også på danskt om nogen forstår

---

### Post by Staraloppan on 2007-02-04
This is an screenshot

---

### Post by Bachstelze on 2007-02-04
You need to create an extended partition, which you will create your logical partitions in.

---

### Post by Staraloppan on 2007-02-04
> **HymnToLife said:**
> You need to create an extended partition, which you will create your logical partitions in.

HOW do i do that?

---

### Post by Staraloppan on 2007-02-04
Ok, i figured THAT oute, but now it's complaining about i have chosen no file system, WHAT it that?!?!?!?!

---

### Post by Staraloppan on 2007-02-04
Ok, in this subject i REALY need some help ASAP!:confused: :confused: 

321 GiB is my files
8 GiB is winXP backup install
4 GiB is what i want to swap to be
10 GiB Where i want to install Ubuntu
30 GiB Windows Xp Media cernter

---

### Post by Staraloppan on 2007-02-04
Do i need to define the other drivers and what they are for?

---

### Post by Rui Pais on 2007-02-04
> **Staraloppan said:**
> Do i need to define the other drivers and what they are for?

No you don't need to define other drivers. It only needs your swap and /. 
But you can, if you want, redefine sizes of partitions. 4G for swap is a lot, maybe 13G for / and 1G (or even less) for swap would be better. 
And/or you can define an separate home partition. Thats generally a good idea and could save a lot of trouble later.

---

### Post by louieb on 2007-02-04
You don't need to define the other partitions (drives that windows stuff). But if you want Ubuntu to read the data in those partitions this is the easiest place to set that up.

---


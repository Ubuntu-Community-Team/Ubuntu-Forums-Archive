---
title: "Partitioning problems with ubuntu feisty"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ToNeZ on 2007-05-27
i finally boot in the live cd and im installing it... the problem its that i have vista in the hard drive and cannot format the disk, i want to dual boot, so, im in the partitioning section of the installer and i dont know what to do now... its a bit different from the edgy installer...

can someone explain me what to do from here? i already click the manual step...

---

### Post by floke on 2007-05-27
From what I've read you shouldn't use GParted to partition Vista - you should use the Vista partitioner, else Vista itself will get borked.

---

### Post by ToNeZ on 2007-05-27
so i gotta log on in vista... partition the disk in vista and come back and install ubuntu?

---

### Post by floke on 2007-05-27
Never come across Vista. But from what I read that's how I understand it.

---

### Post by ToNeZ on 2007-05-27
ok imma see what i can do... thanx


anyone else with another tip or recomendation??

---

### Post by confused57 on 2007-05-27
Steve.K is right...use Vista's partitioner, here's a guide:
[http://www.pro-networks.org/forum/viewstory.php?t=78111](http://www.pro-networks.org/forum/viewstory.php?t=78111)

---

### Post by ToNeZ on 2007-05-27
the vista partitioning tool dont work right... anyone know a software to make partitions?

---

### Post by ugm6hr on 2007-05-27
> **ToNeZ said:**
> the vista partitioning tool dont work right... anyone know a software to make partitions?

Really?  Not even just to shrink the VIsta partition?  

Because that's all that is required - Ubuntu will create the new partition and swap for you from "free/unpartitioned space" if you use the Guided install (largest continuous free space).

Unfortunately, I understand that Partition Magic (the usual Windows partitioner) doesn't work in Vista.  Uncertain about GParted use with Vista...

---

### Post by smoker on 2007-05-27
what size are you trying to shrink your vista partition to? i believe that vista won't let you shrink it's own partition to under around 40GB.

been told this, though, not sure if it is fact or not

---

### Post by ugm6hr on 2007-05-27
> **smoker said:**
> what size are you trying to shrink your vista partition to? i believe that vista won't let you shrink it's own partition to under around 40GB.

been told this, though, not sure if it is fact or not

Definitely not true for Vista Home Basic.  I had that on my laptop before I wiped it.  But before I did, I shrunk it from 25 to 18GB (initially planned dual boot with Vista - but now installed XP/Ubuntu).  Interestingly, Acer shipped my laptop with two 25GB partitions (with 10GB recovery).  Which is perfect for easy dual-booting.

---

### Post by smoker on 2007-05-27
> **ugm6hr said:**
> Definitely not true for Vista Home Basic.  I had that on my laptop before I wiped it.  But before I did, I shrunk it from 25 to 18GB (initially planned dual boot with Vista - but now installed XP/Ubuntu).  Interestingly, Acer shipped my laptop with two 25GB partitions (with 10GB recovery).  Which is perfect for easy dual-booting.

thanks for clarifying that, good to know:D

---

### Post by ToNeZ on 2007-05-27
nop... i click to rezise the partition and an error pops up tell me that the operation cant be completed... im using vista bussines

---

### Post by smoker on 2007-05-27
just a suggestion, have you defragged the drive, maybe if data is scattered all over the partition it won't attempt it?

---

### Post by ToNeZ on 2007-05-27
> **ugm6hr said:**
> Really?  Not even just to shrink the VIsta partition?  

Because that's all that is required - Ubuntu will create the new partition and swap for you from "free/unpartitioned space" if you use the Guided install (largest continuous free space).

Unfortunately, I understand that Partition Magic (the usual Windows partitioner) doesn't work in Vista.  Uncertain about GParted use with Vista...

it doesn say that in the installer of ubuntu it says guided for the hard drive , for my external hard drive and nothing more, i tried to install it on the external disk and it wont let me or i dont know how

---

### Post by ugm6hr on 2007-05-27
> **ToNeZ said:**
> it doesn say that in the installer of ubuntu it says guided for the hard drive , for my external hard drive and nothing more, i tried to install it on the external disk and it wont let me or i dont know how

Which version are you using?  I installed only a couple of weeks ago - and I'm sure that there were 3 options - Guided (entire disc), Guided (free space) and Manual.

---

### Post by ToNeZ on 2007-05-27
im using the current one 7.04 feisty fawn, i downloaded i it  friday

---

### Post by ToNeZ on 2007-05-27
imma boot the live cd and take a picture of the partition part so u can tell me wait a couple of mins

---


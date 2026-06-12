---
title: "Dual booting from Feisty"
date: 2007-11-04
forum: Apple Intel Users
---

### Post by God of the Meeps on 2007-11-04
I attempted to dual boot from Mac OS X, but, I guess I messed up somewhere, and now I can only run Feisty. Does anyone know how to do a dual boot *from* Feisty?

---

### Post by cyberdork33 on 2007-11-04
> **God of the Meeps said:**
> I attempted to dual boot from Mac OS X, but, I guess I messed up somewhere, and now I can only run Feisty. Does anyone know how to do a dual boot *from* Feisty?
What do you mean? did you take over the entire disk or something?

---

### Post by God of the Meeps on 2007-11-04
Well, I partitioned the hard drive (using the Feisty cd), gave it 100GB, let it install, but I couldn't boot Mac OS X after that.

---

### Post by cyberdork33 on 2007-11-04
> **God of the Meeps said:**
> Well, I partitioned the hard drive (using the Feisty cd), gave it 100GB, let it install, but I couldn't boot Mac OS X after that. _How_ can you not? do you not ever get the option? if you do, when you select it what happens? Are you holding ALT on startup?

---

### Post by God of the Meeps on 2007-11-04
I held down the ALT key, but when it shows the hard drive screen, there is only a 'Windows' hard drive shown, no Mac OS X.

---

### Post by God of the Meeps on 2007-11-10
I put in the MAC OS X install CD, followed the instructions to the 'select hard drive' but there was no hard drives.

---

### Post by cyberdork33 on 2007-11-10
> **God of the Meeps said:**
> I put in the MAC OS X install CD, followed the instructions to the 'select hard drive' but there was no hard drives.
I think you overwrote your OSX partition somehow. you will have to use diskutility to repartition the disk.

---

### Post by God of the Meeps on 2007-11-11
I think I did as well, could you tell me how to use diskutility?

---

### Post by cyberdork33 on 2007-11-11
> **God of the Meeps said:**
> I think I did as well, could you tell me how to use diskutility?

It is the partitioning tool on the Mac OSX install disc.


Create your partitions before reinstalling.

When you are ready to install Ubuntu, start the partition editor. Delete the partition you made for Ubuntu, and start the installer, telling it to use free space.

---

### Post by God of the Meeps on 2007-11-11
But how do I access it?

---

### Post by cyberdork33 on 2007-11-11
on the Mac OSX install disc...

There are menus after booting the OSX Install disc, explore them

---

### Post by God of the Meeps on 2007-11-12
I only created one partition, that means that I installed it wrong... right?

---

### Post by cyberdork33 on 2007-11-13
> **God of the Meeps said:**
> I only created one partition, that means that I installed it wrong... right?

I don't know it depends on your intentions.

I would create a couple, one for OSX, and one for Ubuntu (just make it the size you want for all linux partitions).

Then you can install Ubuntu by booting the install disc, deleting the Ubuntu partition, starting the installer and choosing to install to the free space. 

If you wanted to use bootcamp to resize your OSX partition you can make just one and then resize with Bootcamp. The of the process is the same.

I would suggest partitioning upfront though.

---

### Post by God of the Meeps on 2007-11-20
How is it possible to get BootCamp anymore? I don't have it currently, and I thought that the only way to get it now is through Leopard.

---


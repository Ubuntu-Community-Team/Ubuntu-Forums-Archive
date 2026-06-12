---
title: "partioning a already used drive"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Venom_Man on 2008-01-02
i have a 80gb hardrie in my laptop and i want to install ubuntu on it. I have around 50 GB left and i want to give ubuntu 20 of it. My question is how do i create a new partion of 20 gb for unubtu. i using a live cd and i tryed reading other post but could find the right answer. From what i have i read i have to find my os X partion and reduce the size of it from 80 gb to 60 gb then creat a new one of 20 gb for ubuntu i would try doing this with out asking but i dont want to loose all of my stuff.

---

### Post by thelatinist on 2008-01-02
The installation program will do this all for you.  Just boot to the live CD, run the installer, and follow the instructions.

---

### Post by Saint Angeles on 2008-01-02
first thingL in windows, defragment your hard drive, this will (kind of) put your files together making it easier to partition.

when you boot the live CD of Ubuntu, the partitioner will have an option that reads like "Guided, resize partition - use available space"

just set the size to 20GB or so and you'll be good.

---

### Post by Venom_Man on 2008-01-02
i got to this part and i can only do it automatically (which will erase my wole drive) or manually. this is where i get stuck.

---

### Post by Saint Angeles on 2008-01-02
did you defrag first?

its a windows flaw

---

### Post by Venom_Man on 2008-01-02
also im using 7.04 cause im on a ppc

---

### Post by thelatinist on 2008-01-02
> **Saint Angeles said:**
> first thingL in windows, defragment your hard drive, this will (kind of) put your files together making it easier to partition.

I think you missed the part where he's using OS X.  Therefore he can skip the defragmenting step and just go to the installer and choose guided, etc.

---

### Post by thelatinist on 2008-01-02
It doesn't give you an option "Guided - resize the partition and use the freed space"?

---

### Post by Saint Angeles on 2008-01-02
> **thelatinist said:**
> I think you missed the part where he's using OS X.  Therefore he can skip the defragmenting step and just go to the installer and choose guided, etc.

how embarassing...

---

### Post by Venom_Man on 2008-01-02
> **thelatinist said:**
> It doesn't give you an option "Guided - resize the partition and use the freed space"?
  nope i just have guided use entire disk  and guided use the largest continuouse free space

---

### Post by CCNA_student on 2008-01-02
You should be able to do it manually. Just create a Linux swap partition, about two and a half times the amount of RAM you have, and then create the partition that you install Linux on. Make sure you format that partition as ext3. And I picked / as the mount point. If you do not pick a mount point it will not let you go further. I hope that this helps you.

         Sin Cere,

          CCNA

---

### Post by Venom_Man on 2008-01-02
i got and error that say support for hfs+ is not et supported

---

### Post by Saint Angeles on 2008-01-02
is there a different version of Ubuntu thats optimized for Mac?

---


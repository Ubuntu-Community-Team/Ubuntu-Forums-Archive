---
title: "ready to switch"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by bella96793 on 2007-07-06
hello, I want to install ubantu studio edition, how big are the partitions supposed to be and what do I format it to (ext3,ext2?) really new to linux . . . thanks :)

---

### Post by Ek0nomik on 2007-07-06
If you just want Ubuntu, you need EXT3 and Swap.

Swap should be around 1.5 - 2 times the size of your ram.  (Ex:  You have 1GB of RAM, thus you want to make 2GB of Swap)

The rest can be EXT3.

Make the EXT3 partition on the front of the drive, and Swap last.

---

### Post by Majorix on 2007-07-06
Doesn't Ubuntu Studio have guided partition? Ubuntu does and you don't even have to touch it yourself, the comp will handle everything.

---

### Post by bella96793 on 2007-07-06
so ? 1.local disk (vista) 100g ntfs
 
       2.recovery 1g ntfs

       3.linix-swap 1g

       4.ext3 (ubantu)  5.5g

is this good enough space, and will it let me still boot vista?

---

### Post by Istonian on 2007-07-06
I would put more space on the ubuntu partition because that is the maximum space you will be able to use, but it's your preference. That looks good.

---

### Post by bella96793 on 2007-07-06
regular ubuntu on the live cd finds everything I think, that my computer can do i.e. recognition of hardware 
but I don't know how much ram I have

---

### Post by bella96793 on 2007-07-06
1.local disk (vista) 100g ntfs

2.recovery 1g ntfs

3.linix-swap 1g

4.ext3 (ubantu) 6g 

is this better?

---

### Post by Ek0nomik on 2007-07-06
> **bella96793 said:**
> 1.local disk (vista) 100g ntfs

2.recovery 1g ntfs

3.linix-swap 1g

4.ext3 (ubantu) 6g 

is this better?

6GB for your Ubuntu drive isn't very much.

Remember, that local disc of 100g is for Windows only, not Ubuntu.

---


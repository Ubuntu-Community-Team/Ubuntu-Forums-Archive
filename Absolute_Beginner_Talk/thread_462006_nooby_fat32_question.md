---
title: "nooby fat32 question"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by superwazn on 2007-06-02
whats the difference between w95 fat32(LBA) and hidden w95 fat32?  i wanted to partition this drive with fat32 and i dont know this 'w95' of '(LBA)' stuff.

---

### Post by BaffledMollusc on 2007-06-02
> **superwazn said:**
> whats the difference between w95 fat32(LBA) and hidden w95 fat32?  i wanted to partition this drive with fat32 and i dont know this 'w95' of '(LBA)' stuff.

LBA is Large Block Addressing, and is a newer way of addressing sectors on a hard drive. As far as I know, all HDDs these days support LBA.

I have no idea what "hidden w95 FAT" is. But why is it important? What are you trying to do? As far as I can remember, if you do the partitioning as part of the Ubuntu install process you can just choose "FAT 32" as a partition type, without worrying about anything else.

Edit: When I say newer, I mean any hard drive with capacity measure in GB rather than MB. So perhaps "not really ancient" would be a better description than "newer" :)

---

### Post by Inxsible on 2007-06-02
Hidden generally refers to a partition that your system company (Dell, HP, Sony etc) has created to put in the recovery data in case of some screw up that occurs. This will most definitely be for Windows, unless you bought a computer with some other OS pre-installed.

Its *hidden* from the user as in, when you log into Windows, you wont be able to see this partition or even if you see it, you will not be able to access it.

---


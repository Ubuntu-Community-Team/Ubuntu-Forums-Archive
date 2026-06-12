---
title: "GRUB boot loader error 17 again !!!"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by RedKing on 2006-06-17
Hi

I have been following the other posts on this topic and still cant get a fix.

My machine has a raid 0 300GB hard drive ( its actually 2 X 160).
I had windows XP on the system and blew it all  away with the Ubuntu install.

How do fix this error?

Rgs
Redking
:confused:

---

### Post by RedKing on 2006-06-17
running sudo fdisk -l
i get :

Device boot	Start		End 	Blocks		Id 	System
/dev/sda1      	1     		9388	75409078	83	Linux
/dev/sda2      	18315    	19452	9140985		5	Extended
/dev/sda3      	9389     	18314	71698095	83	Linux
/dev/sda5      	18696    	19452	6080571		82	Linux swap / solaris
/dev/sda6      	18315    	18695	3060319		82	Linux swap / solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 255 heads, 63 sectors etc

Disk /dev/sdb doesn't contain a valid partition table.

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
I see from the above that i have installed linux twice ?

When i try to get to Menu.lst it opens as an empty file !

Rgs

Redking

---

### Post by raptros-v76 on 2006-06-17
you need to reinstall grub. i dont know how to do that.

---

### Post by darkali on 2006-06-17
You need to restore the GRUB.

1. Boot-up computer into Ubuntu Installation CD
2. At "boot:" prompt, add "rescue" to the argument 
boot: rescue
3. Follow the instructions on screen.

Now in the Terminal type:
```
grub-install /dev/sda1
```

---

### Post by RedKing on 2006-06-17
How do i get the boot prompt form the live cd

As in how and where do i enter in the boot: rescue parameter ?

---

### Post by RedKing on 2006-06-17
Got to the boot: prompt

When i enter rescue at the prompt i get the following error message

Could not find kernel image : rescue


Any ideas

---

### Post by MountainX on 2008-01-15
I am told that the live CD doesn't have the rescue kernel. You will need to use the alternate CD.

---


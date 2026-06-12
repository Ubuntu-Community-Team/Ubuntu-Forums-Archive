---
title: "Unknown Partition help"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by aznkid8706 on 2007-03-17
This is my first time installing any linux system. :)  I kinda reached a road block on the partitioning section of the installation.

I have a 120 GB HD with windows XP.  I want to dual boot and the Dell comp came with a hidden recovery partition i want to keep incase i want to do a clean setup of windows in the future.  I then found that I can only make a max of 4 partitions. So when i make another partition for unbuntu, I noticed i now had a 4 partitions and i need another for a swap for unbuntu. The mystry partition that is preventing me from making the swap is a tine 47 MB FAT partition.  I used Windows disk management service and it stated it has a EISA Configuration. . the description said  EISA -a "original equipment manufacturer (OEM) partition"  
Well, for Unbuntu i need a "/" and a "swap" apparently, but this tiny partition is preventing me from making a swap partition.  **Is it safe to delete?** :confused: :confused: 

What i did exactly:  Shrunk windows partition to 65 GB. Created a 43GB unallocated partition. A 4.63 GB partition that i'm assuming is the windows restore partition. A tiny 47MB partition that i don't know wat it is.  That 4 partitions!  I can't make a swap! :mad: 
Another problem is that if i am to delete the 47 MB partition i can't combine it with the 43GB unallocated space I already have.  Gparted puts them at opposite ends.  Wat to do??? :confused: 


Thanks for your help!

---

### Post by STREETURCHINE on 2007-03-17
I Deleted Mine Because I Just Uninstall Windows Formated The Whole Patition And Did A Reinstall Of Windows

But You Could Just Make A Logical Partition And Use That For Ubuntu

---

### Post by aznkid8706 on 2007-03-17
Wat is tat?

---

### Post by mikewhatever on 2007-03-17
Why not make your Ubuntu partitions extended/logical? In no way do they need to be primary ones, and you won't have to delete anything.

---

### Post by AtrejuT on 2007-03-17
you can create an extended partition as the 4th partition you are allowed to make. this is a meta-partition, meaning that in this extended partition you can create new partitions for / and swap without having to worry about the 4-partition limit.

does this make sense?

atreju

---

### Post by aznkid8706 on 2007-03-17
Yeah i saw that in the setup, but couldn't figure how to use it.  I right-clicked the unallocated space and selected new.  Then I changed the menu from primary to extended.  Beyond that all i saw was the same deal but now the partition had a dropdown menu.  How do i create a swap after this step?   I feel like i'm so close! I can feel it!

---

### Post by Kateikyoushi on 2007-03-17
Create two partitions in it 1GB for swap filesystem swap and the rest as ext3 for the system.
Read this dualboot installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

---


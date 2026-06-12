---
title: "Resize main partition"
date: 2009-04-20
forum: Apple Hardware Users
---

### Post by N_Nick on 2009-04-20
Hey everyone,

I dual boot Linux and OSX and i want to resize my Ubuntu partition - its currently 10GB. Is it safe to resize the OSX partition to make up more space for Ubuntu? And if so, how much smaller can i actually make it? (I only use about 63GB out of the 170GB partition).

By the way gparted shows a 1.2GB HFS+ partition labelled Linux Swap (screenshot below). That cant be correct right?

---

### Post by cyberdork33 on 2009-04-20
> **N_Nick said:**
> I dual boot Linux and OSX and i want to resize my Ubuntu partition - its currently 10GB. Is it safe to resize the OSX partition to make up more space for Ubuntu? And if so, how much smaller can i actually make it? (I only use about 63GB out of the 170GB partition).Make a Backup! You can do what you are saying. You can make the OSX partition as small as you want to, though the closer that you make it to the amount of used space, the more likely you are to have an issue. 

> **N_Nick said:**
> By the way gparted shows a 1.2GB HFS+ partition labelled Linux Swap (screenshot below). That cant be correct right?
It's just the label. You can label it what you want. Do you even use that second HFS+ partition for anything?

---

### Post by N_Nick on 2009-04-21
Thanks for your reply cyber.

> **cyberdork33 said:**
> 
It's just the label. You can label it what you want. Do you even use that second HFS+ partition for anything?

No, i dont even think i created that myself. I was just making sure so i can get rid of it.

---

### Post by N_Nick on 2009-04-21
Sorry for double posting but since this is somehow related i thought its better to ask here.

I ordered today a 30GB Solid State Drive (SSD) along with 4GB of memory for my Linux Macbook Pro.

1) With some help from Google i found out that its better to use a non journaled filesystem on SSD's. Anyone with some experience (or not) who can help on choosing the right FS?

2) Which is the best solution in order to use all 4GB of RAM? (x64 etc)

Im on a 4,1 Macbook Pro (Penryn)

Cheers

---

### Post by cyberdork33 on 2009-04-21
> **N_Nick said:**
>  1) With some help from Google i found out that its better to use a non journaled filesystem on SSD's. Anyone with some experience (or not) who can help on choosing the right FS?
ext2 is not journaled.

> **N_Nick said:**
> 2) Which is the best solution in order to use all 4GB of RAM? (x64 etc)
I think you have to use a 64bit OS to use all 4GB of RAM.

---

### Post by N_Nick on 2009-04-28
Edit: Moving thread to General help.

---


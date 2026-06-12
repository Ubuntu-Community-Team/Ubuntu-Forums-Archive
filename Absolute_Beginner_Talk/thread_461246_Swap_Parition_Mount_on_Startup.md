---
title: "Swap Parition Mount on Startup"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-06-01
Hi, i created a swap partition earlier with the gigabyte of backup space i had on my hard drive. How can i mount this partition on startup?

---

### Post by Cypher on 2007-06-01
You used the "mkswap" command to create this swap space? If so, you'd want to add this new entry to your /etc/fstab file. You will need to use the "vol_id" command on the particular you just created for SWAP, once you find that add something like the following to the /etc/fstab file
```

UUID=<UUID goes here> swap swap defaults 0 0

```

---

### Post by Inxsible on 2007-06-01
Just curious..
 
why would you want to mount the swap drive?  you cannot store any information on it yourself anyway as its used by the kernel. It doesn't have any file system on it either

---

### Post by Cypher on 2007-06-01
Technically, it does have a 'swap' filesystem on it. :)

---

### Post by Inxsible on 2007-06-01
> **Cypher said:**
> Technically, it does have a 'swap' filesystem on it. :)
 
Unusable by the user however :)
 
Wow...thats some alliteration there !

---

### Post by Cypher on 2007-06-01
Yeah un-usable by the user, but if your system is low on memory or something, swap space is vital for system usage. Most systems with 1GB or more system ram will almost  never use swap space..

---

### Post by Inxsible on 2007-06-01
yep, so whats the point in mounting the swap drive if you will never be able to use it anyway.
 
If you do mount it, there is always a possibility that you will create locks, if the kernel is using the swap and you fire up nautilus and browse to that swap drive.
 
Not that it WILL happen, but it could !

---

### Post by bobbocanfly on 2007-06-02
I am not trying to mount it to put any data on it. It wont swapon at startup so i need to go into gparted every time and click swapon for it to work. I have a rubbish processor and only 512mb of ram so thats why i want a swap space.

btw. i made the swap partition in gParted

---


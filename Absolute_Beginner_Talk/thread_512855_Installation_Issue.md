---
title: "Installation Issue"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Donnie Darko on 2007-07-29
I recently wiped my drive and installed Vista Ultimate, but wanted to reinstall ubuntu as I like it better. As for getting a dual boot, I'm having some issues. I ran the Gparted live CD and gave ubuntu a 30 GB partition, and I'm trying to run the install onto the partition, but I keep getting the error "No root file system defined"  



[IMG]http://img.photobucket.com/albums/v451/ska7245/Screenshot-2.png[/IMG]



Does anyone know why this is happening?

Cheers
-Donnie

---

### Post by moffa on 2007-07-29
You need to set a root partition for ubuntu to install in. Looking at your screen shot, I think you want to change the mount point for /dev/sda2 from /media/sda2/ to /

---

### Post by Donnie Darko on 2007-07-29
ok, I changed it to /, but I got a message like this....



[IMG]http://img.photobucket.com/albums/v451/ska7245/Screenshot-2-1.png[/IMG]

thanks
Donnie

---

### Post by jimrz on 2007-07-29
> **Donnie Darko said:**
> ok, I changed it to /, but I got a message like this....



[IMG]http://img.photobucket.com/albums/v451/ska7245/Screenshot-2-1.png[/IMG]

thanks
Donnie

place a check mark in the "format?" column for your / partition and proceed. it will then format the partition with bootable flag and / as mount point. also, i would suggest using the ext3 file system

---

### Post by Donnie Darko on 2007-07-29
so how do I create a swap partition? It's asking me that right now. Your advice worked perfectly. 
Cheers.
-Donnie

---

### Post by jimrz on 2007-07-29
> **Donnie Darko said:**
> so how do I create a swap partition? It's asking me that right now. Your advice worked perfectly. 
Cheers.
-Donnie

since you do not appear to have any unallocated space, just change the size of your / partition to "29882" this will leave approx 2 Gb unallocated for the partitioner to use when it makes your swap partition. not sure what your equipment is.  if it is a laptop, make sure that swap is at least 1.5 times your amount of ram to avoid problems when suspend. you can either create a swap partition manually setting whatever size you need (do this for sure if laptop) or the partition will add one on its own determining the size itself.

---


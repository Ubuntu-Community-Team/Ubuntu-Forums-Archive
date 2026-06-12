---
title: "partition permissions"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by tumble on 2007-08-06
Hi, I have a 250GB HDD with various partitions- windows, one called STUFF with my music etc.. and the other two for Ubuntu. I can mount STUFF so I can listen to music and open files but the problem is I cant modify or save files on it. under STUFF properties in permissions the owner is root and it says "you are not the owner, so you cant change these permissions". Is there a way to change this as I want that partition as my main media source?

---

### Post by Inxsible on 2007-08-06
First of all what is the file system on the partition called STUFF ?

If its NTFS, have you installed ntfs-3g to gain write access on the partition?
for ext3 file systems you can change ownership by using the chown command

---

### Post by tumble on 2007-08-06
umm ntfs i guess. since i used it first in windows. I find that i maybe need root password but i didnt make one on install. how do i find it?

---

### Post by nitro_n2o on 2007-08-06
open synaptic and download the NTFS configuration tool 
it will be installed in Applications->system tools 
just check the enable write to NTFS and have fun

---


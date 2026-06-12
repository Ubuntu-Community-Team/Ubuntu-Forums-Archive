---
title: "change ownership of partition"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Vic! on 2008-02-24
Hello i have a separate partition in my HDD and id like to use it to store some videos however when i mount it it says i dont have the proper permissions to write data on it. how do i make it so i can use it? also id like it to "automount" when i boot :) any help is greatly appreciated thank you VERY MUCH!! 

v

---

### Post by zerhacke on 2008-02-24
Edit /etc/fstab and change the options on the mount to rw.

---


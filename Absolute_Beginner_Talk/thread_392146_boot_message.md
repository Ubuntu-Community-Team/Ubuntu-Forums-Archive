---
title: "boot message"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by garymc1 on 2007-03-24
hi there when i boot ubuntu i get a message every so often telling me that 
(hdc1 has been mounted 30 times without being checked - check forced) 
i am new to ubuntu can some one please help many thanks gary

---

### Post by bulldog on 2007-03-24
Nothing to worry about.
It checks your file system every 30 times it gets mounted,to ensure it's clean.

---

### Post by mendingo84 on 2007-03-24
if it says smth about fsck check and gives a warning message like "Last mount in the future" and the booting process hungs for a little, then you should do the following:
> 
sudo vim /etc/fstab


,or use any other text editor as root, and change the last number on each line to 0. (of course, i mean the lines that are not commented with '#')

---


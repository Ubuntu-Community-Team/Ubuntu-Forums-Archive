---
title: "afs on Ubuntu"
date: 2004-11-21
forum: Apple PPC Users
---

### Post by cow_racer on 2004-11-21
Has anyone gotten afs workong on ubuntu?  I was not able to compile the afs module.

---

### Post by Beowolf on 2005-04-06
I just wanted to ping the topic. Anyone successful in doing this?

I have all my work on my school's AFS server and openafs is a must for me. However, I haven't been able to use it under ubuntu. I tried to install openafs-client which needs the afs kernel module. The module source is there in the repository but it doesn;t compile. An alternative is arla. arla client is able to browse afs tree but when it comes to mount afs, the kernel module (even though successfully compiles) is not accepted by insmod.

I had to give up several times on doing this but on the other hand, I know that i was able to use afs under suse 9.1 & 9.2 which both run 2.6.x kernels. There, the kernel module was provided as a compiled rpm. 

Anyway, is there anyone out there who has an idea about this? Ubuntu is the best dist i have used so far, including suse. Although I likes suse, it was a very bulky dist for me with all fancy tools and stuff. I really want to stick with ubuntu especially since I enjoy the nicely themed gnome desktop a lot.

beo.

---

### Post by abhaysahai on 2005-04-15
Hi,
Kindly check my post at [http://ubuntuforums.org/showthread.php?p=133361#post133361](http://ubuntuforums.org/showthread.php?p=133361#post133361)

It explains how to get arla working on Hoary. 

Regards,
Abhay

---

### Post by Beowolf on 2005-04-16
Hello Abhay,

Thanks!!! I tried it and it worked nicely. I now switched back to hoary from debian. Last time I checked that website the guy had the module-source but i couldn;t compile it on my box, with the standard hoary kernel. Appearently, he has compiled the module himself this time. Great Work!!!

thanks again.
beo

---


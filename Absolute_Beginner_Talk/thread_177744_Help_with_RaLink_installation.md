---
title: "Help with RaLink installation"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-16
I have been installing RaLink drivers as per the readme file. I got to:

7> $load

#[kernel 2.4]

# $/sbin/insmod rt61.o

# $/sbin/ifconfig ra0 inet YOUR_IP up



#[kernel 2.6]

# $/sbin/insmod rt61.ko

# $/sbin/ifconfig ra0 inet YOUR_IP up

where I am not sure of, and when I typed:

questa@Questa:~/RT61_Linux_STA_Drv1.0.4.0/Module$ load /sbin/insmod rt61.o
bash: load: command not found
questa@Questa:~/RT61_Linux_STA_Drv1.0.4.0/Module$

i even tried:

sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/

questa@Questa:~/RT61_Linux_STA_Drv1.0.4.0/Module$ sudo cp rt61.ko /lib/modules/questa -r /kernel/drivers/net/
Password:
cp: target `/kernel/drivers/net/' is not a directory: No such file or directory
questa@Questa:~/RT61_Linux_STA_Drv1.0.4.0/Module$

What went wrong?

---


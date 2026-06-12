---
title: "basic steps for manual partition of harddisk"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-02-21
[SIZE="5"]i am very much new to linux,at the first attempt of installation i choose to manually partition my hard disk,as i thought i am well experience in windows it would be easy to me partition hard disk in linux(manually),
but when i had enterd in the partition i didn't get the basic things in my mind they are
what is swap,mount point,home,root etc :(
i am finally interested in creating 6 partitions of my 80GB hard disk space
please help me
i need your suggestion :)
i am very confused:confused:
this is problem of many of my friends [/SIZE]

---

### Post by jan quark on 2008-02-21
first do not use the big font any more

here is a good guide "to plan partitions"

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

here is an graphical installation guide
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jan quark on 2008-02-21
this can be also useful

[http://www.linuxsa.org.au/tips/disk-partitioning.html](http://www.linuxsa.org.au/tips/disk-partitioning.html)

---

### Post by seventhc on 2008-02-21
Swap acts as virtual memory, so if you run out of ram ubuntu will use swap. I usually give it 1 gig, but I could probably use less as I hardly need it. I have the disk space so I always give at least 1 gig. When swap is needed the machine does it for you, once you have the swap partition ubuntu will recognize it and know what to do.
/ is for system files..basically where ubuntu will install to.
I would create a separate /home partition. By keeping a separate /home partition if you ever reinstall can still keep all your files in your /home intact if you want.

May I ask why you want 6 partitions?

---

### Post by phanipalagummi on 2008-02-21
thank you sir,
6 partitions means i want 6 drives
as in windows
sorry if i mean some thing unlogical

---

### Post by seventhc on 2008-02-21
I know what 6 partitions means, I was asking why?
Do you want 6 linux specific partitions, or some with NTFS,
You want a dual boot?
How many do you want for linux,
how many for windows?

---

### Post by Duck2006 on 2008-02-21
This is the documentation from gparted witch you would use to partition your drive/s in ubuntu.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by phanipalagummi on 2008-02-22
yes i want 6 specific linux partitions
i dont wont to dual boot
 and what  is the use of  NTFS in linux
please explain me

---

### Post by seventhc on 2008-02-22
In case you were dual booting and wanted extra partitions for windows.

---


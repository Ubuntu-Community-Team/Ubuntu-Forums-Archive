---
title: "Which setup to use for 1 harddrive, 2 partitions?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by denbeau on 2006-10-21
First time installer..
I have a 80gb harddrive with a 47gb primary WinXP partition and a 28gb logical partition. The second I would like to install Ubuntu. 
I'm not sure which choices I need, when I install it? 

Thanks
Denbeau

---

### Post by dbd on 2006-10-21
When you get to step 7 of the install (called Prepare Disk Space), you want to choose the "Manually Edit Partition Table" option.

then just choose the 2nd partition, delete it and make your linux partitions.

For general info on the install see here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and for info on partitioning see here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck :)

---

### Post by raqball on 2006-10-21
I have my partitions as follows:

#1  / (5gb) (system files)
#2  linux-swap (1gb) (emergency memory dump)
#3  /home  the rest of your hd (your free file space)

---

### Post by Sef on 2006-10-21
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---


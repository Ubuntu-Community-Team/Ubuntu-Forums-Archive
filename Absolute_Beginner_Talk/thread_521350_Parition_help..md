---
title: "Parition help."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Dionysus135 on 2007-08-09
My question is that on the Parition guided screen there is one option that says use entire disk and set up LVM.What does LVM stand for?

---

### Post by Inxsible on 2007-08-09
> **Dionysus135 said:**
> My question is that on the Parition guided screen there is one option that says use entire disk and set up LVM.What does LVM stand for?
I think it stands for Logical Volume Manager, meaning it will reside on an Extended partition rather than a primary partition

---

### Post by Cypher on 2007-08-09
LVM is [Logical Volume Management]("http://en.wikipedia.org/wiki/Logical_volume_management"). Should be safe to use it..

---

### Post by Dionysus135 on 2007-08-09
Oh yea one more question.What option should i choose to erase my whole parition and use it?Do i press use entire disk?And if i use entire disk does it erase any viruses spyware and etc. from windows xp?

---

### Post by Inxsible on 2007-08-09
> **Dionysus135 said:**
> Oh yea one more question.What option should i choose to erase my whole parition and use it?Do i press use entire disk?And if i use entire disk does it erase any viruses spyware and etc. from windows xp?

Erase whole partition or erase the entire drive ?

if you choose erase entire "drive" it will not only erase the viruses, it will erase Windows too. do you want to do that ? or are you planning on a dual boot ?

---

### Post by splintercellguy on 2007-08-09
If you select Use Entire Disk then you will entirely wipe out any data and Windows XP from the hard drive. Make sure to backup any data you want to keep.

---

### Post by Dionysus135 on 2007-08-09
well im switching to xubuntu and i just want on OS on the cpu.I really dont need any data from it.So should i use entire disk?

---

### Post by splintercellguy on 2007-08-09
Yes, that's the option you should pick.

---

### Post by Cypher on 2007-08-09
Yes, you would use entire disk if you want only Ubuntu on there. Know that the default partition scheme doesn't break it down into smaller partitions for each component of Linux. Rather, you will end up, likely, with just 2 partitions. One that holds all of Linux and one for swap.

This is not a bad partition scheme, but it is usally a good idea to seperate out the /home partition on it's own so that you can re-install Ubuntu later while retaining all of your personal documents..

---

### Post by Inxsible on 2007-08-09
I agree with Cypher. I would recommend making a different partition for /home

Try these links which detail out the process with illustrations,

[Partitioning]("http://ubuntuforums.org/www.psychocats.net/ubuntu/partitioning")

[Installing]("http://ubuntuforums.org/www.psychocats.net/ubuntu/installing")

---


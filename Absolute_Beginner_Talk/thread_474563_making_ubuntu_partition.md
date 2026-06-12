---
title: "making ubuntu partition"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Tony_w on 2007-06-15
I've allocated 17 GB's to kubuntu on a windows partition. I want to create the partition manually, but I'm having problems doing this. There doesn't seem to be any options for creating the root, swap etc. I've only been able to create a single root or swap and then I've got stuck. How's it done?

Thanks.

---

### Post by antoz on 2007-06-15
Use the live CD, don't go into install, instead open the gnome partition editor and create your partitions with Gparted. Your Ubuntu partition has to be formatted "ext3" and your swap partition "swap"
You can only have 4 primary partitions, after that you have to create an extented partition and logical partitions inside it. Your swap should be at least 1.5 times your RAM, you could also create a separate Home partition this is not necessary though.Hope this helps,A
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by fumduck on 2007-06-15
I think you are having the same problem I had.. which is after you allocate the 17 gb and  and name it  "/"  root directory.. you then edit  '/' that partition and allocate another  say 2 gb of free space and  make it swap.. then you have your root, swap, and windows partition...   Hopefully I understood your question or somebody more knowledgeable answers.. if not maybe this link will help
[http://apcmag.com/dualboot]("http://apcmag.com/dualboot")

---


---
title: "error while instaling ubuntu"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by VIVEK VARDHAN REDDY on 2007-02-11
i get an error saying you can't create more than four primary partitions can any one tell me how to create extended partitions

---

### Post by dckirba on 2007-02-11
I believe the partition editor on the install CD lets you partition logical drives. Anyways, here's a good link for installing: 

For Desktop (live) CD: [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

For alternate CD: [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")
somewhere in the middle of this page, it explains the basics on primary and logical partitions and how to make them with the alternate install CD.

There's also some information on how to plan your partitions:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

I hope this helps,
cheers and have fun,
David K

---

### Post by housam on 2007-02-11
> **VIVEK VARDHAN REDDY said:**
> i get an error saying you can't create more than four primary partitions can any one tell me how to create extended partitions

Delete one of the primary partitions and transfer it to a new extended one. then you can divide it to many logical partitions. ( Use Gparted to do the job. )

---


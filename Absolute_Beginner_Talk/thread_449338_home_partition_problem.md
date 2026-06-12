---
title: "home partition problem"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by namrocks on 2007-05-20
A clean install of 7.04.
 /home (9) gigs
/ (8.5 gigs)
swap (1.5 gigs)

The install goes well. When I boot up and use the Disk Usage Analyzer it says my home directory is full and is only 7.6 MB. I don't understand how this could be.

---

### Post by Kobalt on 2007-05-20
As I understand it you have a separate partition for Home : did you specify well the /home mount point for your Home partition during the install ?

---

### Post by namrocks on 2007-05-20
How do you specify a mount point?

---

### Post by zvacet on 2007-05-20
What does it say in** total filesystem usage** ? I can not tell 100% but almost that dics analyser told you that it scans your disc totaly.In short it does the job.Nothing to be worried about.if you just install OS your disc is emty exept for the space OS takes.You will see that in total filesystem usage.

---

### Post by Kobalt on 2007-05-20
When the installer gets to the partitioning tool, select 'Manual'. You get to a screen where all your partitions and drives are listed. If you click on one and select 'Edit partition' then you can specify a mount point.

PS: In case of a /home partition, make sure the **Format** option is **not selected** if you want to keep your personnal file.

---

### Post by namrocks on 2007-05-20
I selected Edit Partition and for home the default was place at the beginning and ext 3. I left the defaults and just added /home in the bottom box. Was that right? Thanks.

---


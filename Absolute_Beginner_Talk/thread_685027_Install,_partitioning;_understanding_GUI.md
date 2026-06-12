---
title: "Install, partitioning; understanding GUI"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by yc2 on 2008-02-01
I have run Ubuntu for some time now. When I installed I used manual partitioning. A friend of mine is now installing using the guided partitioning and he is asking me the following question. 

In step four of the installation of Ubuntu (using GUI) the following panel appears (my translation from Swedish):
```
Prepare disk space
How do you wish to partition the disk?

Guided. Change size of  &#8230; partition n and make use of the disk-space aquired.
```
Below is a control that you can pull from left to right. Above the control you can read figures (Gigabyte and percent.)

My question is: What can you set here? What is indicated by the Gigabytes? What is indicated by the percentage?

For example: My friend already has WinXP in his computer. When he pulls this control, will the size indicated be the size of his changed (shrunken) XP-partition or will the control indicate the size of the disk space allocated for his (root, swap) new Ubuntu system?

What does the percentage mean? What part is taken from what part to compute the percentage?

Sorry for not having been able to find the answer to this basic question. In forums I have even found contradictory answers. Please help me clarify. I don&#8217;t want to lead my friend astray.

Thanks. :KS

---

### Post by logos34 on 2008-02-01
> **yc2 said:**
> When he pulls this control, will the size indicated be the **size of his changed (shrunken) XP-partition** 

yes.

---

### Post by jleaker01z on 2008-02-01
The slider bar adjusts the size of the existing Windows partition.  So if you adjust the slider to 40gb, that means Windows will have 40gb to work with, and Ubuntu would use the rest.  The percentage is based on the entire disk size.  ie, 40gb of a 100gb drive would read as 40%.

---

### Post by yc2 on 2008-02-01
logos34, jleaker01z

Thank you for quick assistance :popcorn:

---


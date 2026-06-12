---
title: "logical or physical partition"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-09-06
Hi,
I have just installed Xubuntu on my trash at home. I have been using Ubuntu in the office for a while though.
I have a question at the partition part. whenever I created a new partition, I was asked whether that partition will be logical or physucal partition? I gave random answers. What are the differences between those two and what should my answer have been?
I created partitions for
/
/swap
/boot
/var
/usr
/tmp
/home

---

### Post by bodhi.zazen on 2006-09-06
A HD can have only 4 partitions, each one is called a primary partition.

1 primary partition can be made into an extended partition.

An extended partition can have 4+ logical partitions.

To Ubuntu primary/logical is irrelevant.

Some OS (Windows, BSD will not install into a logical partition and thus must be installed on a primary partition.

---

### Post by amo-ej1 on 2006-09-06
Indeed, the only thing that really matters is that one of your four primary partitions should be an extended one. The are numerous people creating four primary partitions that get stuck when they want to create a fifth on.

---


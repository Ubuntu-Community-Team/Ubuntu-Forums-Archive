---
title: "need help installing"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by f250ld on 2006-11-10
when I go to install, after the partition page, and i tel it to install, I get and error that says "No root file system is defined." how do i define the root file system?

---

### Post by an.echte.trilingue on 2006-11-10
on the partition page, the partition that you want ubuntu to live on needs to be mounted at "/"

[Be sure to read this page]("https://help.ubuntu.com/community/Installation")

---

### Post by f250ld on 2006-11-10
in which step 5 or 6? i just can't seem fo find where it wants me to declear the root directory

---

### Post by bulldog on 2006-11-10
For Ubuntu you need at least two partitions,your / [root]  and your swap.

It's recommended to make a separate /home partition to save your data,but that's not a must have.
When you have this two made you can proceed with the install,if not,it won't install because it has no space to use.

---


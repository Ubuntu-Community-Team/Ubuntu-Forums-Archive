---
title: "Email Storage Sharing"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Bungo Pony on 2007-03-28
Has anybody successfully been able to share their email storage between OSes?

I'm running Thunderbird in both Windows and Ubuntu, and I would like to be able to check my email under either OSes. But I would also like to be able to see what mail I have sitting on my hard drive in either environment. I tried making them store and load from the same directory (ext3 partition) but it's complaining in Linux.

Is there any way to do this? I know it would work in Netscape 4.

---

### Post by halitech on 2007-03-28
windows won't see ext3, you'd be better off setting up a small fat32 partition and saving the folder there

---

### Post by h0ax on 2007-03-28
I agree with halitech, fat32 partitions are great because both Linux and Windows can read/write to the drive without having to do too much extra effort.  NTFS (XP FileSystem) is a little picky about what can write to it (you have to set this up specifically if you want to write to NTFS drive in Linux)

---

### Post by machoo02 on 2007-03-28
> **halitech said:**
> windows won't see ext3, you'd be better off setting up a small fat32 partition and saving the folder there
Unless you install the [ext3 driver for Windows]("http://www.fs-driver.org/")

---

### Post by halitech on 2007-03-28
> **machoo02 said:**
> Unless you install the [ext3 driver for Windows]("http://www.fs-driver.org/")

guess thats what I get for not using windows :(

wait, what am I saying? I don't have to use windows anymore :)

---

### Post by Bungo Pony on 2007-03-28
I installed the ext3 drivers in Windows and they work wonderfully.

I can only guess that Thunderbird uses a different file system on each OS. Can anybody confirm?

---

### Post by billmeek on 2007-03-29
To resolve this issue I switched from pop3 to Imap (server stored mail).  Now I can check email under either OS on my primary laptop, on another machine, or even use a web email client.

---


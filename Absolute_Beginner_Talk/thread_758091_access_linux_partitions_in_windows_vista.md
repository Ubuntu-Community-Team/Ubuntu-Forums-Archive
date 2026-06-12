---
title: "access linux partitions in windows vista"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by sgleo87 on 2008-04-17
I dual boot Windows Vista Business and Ubuntu Gutsy. I need read and ideally also write support for my linux partitions under Vista so I can open and save Office 2007 files that I have in Ubuntu. I have seen some guides for Windows XP but none for Vista. Anybody know how to do this?

---

### Post by dje on 2008-04-17
Have a look [here]("http://www.fs-driver.org/index.html"), if you read down the page it says see the FAQ for ext3 filesytems. Specifically [this bit of the FAQ]("http://www.fs-driver.org/faq.html#acc_ext3"). This supports vista

hope that helps,
dje

---

### Post by sgleo87 on 2008-04-17
awesome, thanks that worked perfectly!

---

### Post by dje on 2008-04-17
You're welcome :)

---

### Post by stchman on 2008-04-17
> **sgleo87 said:**
> I dual boot Windows Vista Business and Ubuntu Gutsy. I need read and ideally also write support for my linux partitions under Vista so I can open and save Office 2007 files that I have in Ubuntu. I have seen some guides for Windows XP but none for Vista. Anybody know how to do this?

I use this:

[http://www.diskinternals.com/linux-recovery/](http://www.diskinternals.com/linux-recovery/)

It works for both XP and Vista.  It allows only reading not writing to EXT3 drives.

---


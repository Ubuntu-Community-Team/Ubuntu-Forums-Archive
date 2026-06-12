---
title: "XP can't boot...help"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by skotina on 2007-11-02
Hi, I am totally new to Linux...
On my computer, I have Win XP. I just installed Ubuntu, and it works fine... But when I tried to boot XP it starts and then it says: Autochk program not found - skipping AUTOCHECK, and the computer restarts and goes back to the boot meny...

I have found that this problem is caused because of Partition Magic 8, and is called Hidden NTFS. And it says it can be fixed with fdisk. How do I start fdisk in linux???

Thanx

---

### Post by ddrichardson on 2007-11-02
Open a terminal and type```
fdisk
```However, if you are uncomfortable with the terminal boot the live install cd and use gparted to unhide the partition - if that is what PM is advising.

---


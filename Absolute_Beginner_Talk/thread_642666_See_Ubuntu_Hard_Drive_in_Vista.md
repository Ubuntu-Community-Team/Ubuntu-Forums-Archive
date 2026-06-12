---
title: "See Ubuntu Hard Drive in Vista"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Lanc1988 on 2007-12-16
I have two hard drives in my computer.. vista is installed on one of them (C: ) and ubuntu 7.10 is on the other one (F: ).

When I boot into ubuntu i can go to computer and see both hard drives and when i try to open the vista one, C:, it does something about mounting it and then im able to view and access all the files on it.. but when I boot into vista and go to my computer, it only shows the hard drive with vista, the one with ubuntu doesnt even show up. Is there a way I can get it to show up so I can copy some files from ubuntu to vista without having to use a flash drive to transfer the files?

---

### Post by seventhc on 2007-12-16
If you go to Applications>Add/Remove...make sure its set for 'all open source applications' in the upper right corner then do a search for ntfs and you should find **NTFS Configuration Tool**. This should let you read and write to your windows partition.

---

### Post by p_quarles on 2007-12-16
> **seventhc said:**
> If you go to Applications>Add/Remove...make sure its set for 'all open source applications' in the upper right corner then do a search for ntfs and you should find **NTFS Configuration Tool**. This should let you read and write to your windows partition.
That tool allows you to use the Windows drive from Ubuntu, but the OP is asking the opposite situation.

Lanc1988: You'll need a tool called ext2fs, which'll allow you to access the Ubuntu partition from Windows:
[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

---

### Post by seventhc on 2007-12-16
oh...I totally missed that. Thank you, I'll start reading more carefully
In my mind nobody wants to boot into windows lol

---


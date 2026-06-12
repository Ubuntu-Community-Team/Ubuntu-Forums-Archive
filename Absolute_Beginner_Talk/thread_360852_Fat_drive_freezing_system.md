---
title: "Fat drive freezing system"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by cnich23 on 2007-02-13
I have wanted to try ubuntu again since the community is now flourishing.  Coming from a work pc with windows XP I have two drives ...

80GB SATA - PRIM
160GB IDE - SEC

Before I installed Ubuntu I converted the 160GB drive from NTFS to FAT with partition magic (data remained on drive)

After mounting the fat drive the system will freeze randomnly, sometimes 1 minute sometimes 10, but if I do any activity on the drive such as use Amarok, all my music is on that drive, the system will freeze almost instantly

My patience is started to dwindle down now and erasing the drive is not an option without backing it up, except for the fact I can only copy a few files before the system freezes (it does not always freeze on the same file)

Is there anyway, (im doubting), to convert fat to ext3 with data intact?  If not what are my options for trying to backup the data on the fat drive without reinstalling windows?

---

### Post by Jabran Asghar on 2007-02-13
Hi,

May be you can try booting from Ubuntu Live CD, and see if accessing the drive still freezes the system. If not, then you can mount your other ext3 drive and copy data from FAT to ext3. If space is the problem, you can use "tar" to make archive and compress.

Hope this helps.

Jabran

---


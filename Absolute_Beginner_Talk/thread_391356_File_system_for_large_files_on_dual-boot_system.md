---
title: "File system for large files on dual-boot system?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by HumbleGod on 2007-03-23
So within the previous week or so I've started making a transition from XP to Ubuntu, thanks in no small part to the help I've received on these forums. When I installed Edgy, I went ahead and created a FAT32 partition so that I had a partition which both XP and Ubuntu could write to. I would like to expand this partition so that I can manipulate additional files from both systems; however, a lot of the activities I've been using my Windows system for have involved large file types (4-5 GiB), and I understand that the FAT32 system has a 4 GiB limit.

So basically my question is: Is there a file system out there that can be read from AND written to in both Ubuntu and XP that can handle larger files?

---

### Post by Obor on 2007-03-23
In past I've used ext3 (same as ubuntu) for my shared files. On Windows side you install [fs-driver]("http://www.fs-driver.org/") to recognize this partition/s (it will add it as another drive i.e. e or f etc.) It reads and writes pretty well. I've never had any problems.

---

### Post by HumbleGod on 2007-03-23
That may be just what I need, so I'll give it a go. Thanks, **Obor**.

---

### Post by mdsmedia on 2007-03-23
There is also a program on the Linux side that will read/write to NTFS (the Windows XP file system).

The name escapes me, but I understand it is now a stable release.

I've been thinking of installing it and making my current FAT32 partition Ext3. Then with the XP program and the Linux program installed on either side I can read/write from either, but I'd rather have Ext3 than NTFS as the shared system.

---

### Post by anaconda on 2007-03-23
> **Obor said:**
> In past I've used ext3 (same as ubuntu) for my shared files. On Windows side you install [fs-driver]("http://www.fs-driver.org/") to recognize this partition/s (it will add it as another drive i.e. e or f etc.) It reads and writes pretty well. I've never had any problems.

It is very reliable, but there is ONE problem. Before you copy a file to your ext3 partition with it make sure there is enough room in the drive. The only problem I ever had with the ext3-driver was when I tried to copy a file which didn't fit to the drive..

Oh.. and even that problem was automatically fixed with the next boot to ubuntu..

---


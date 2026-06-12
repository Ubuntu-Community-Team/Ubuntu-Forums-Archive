---
title: "NewBie : How Can I Write To NTFS (Dual Mode - Read/Write)"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by 7mm on 2007-02-18
Hi THere Every One. I'm Using KUBUNTU 6.10 With WindowsXP As My Primary OS. Since New To Linux, It Has To Be Dual Boot. My Problem Is Whn Ever I Try To Put Any File From Linux Partition (ReiserFS) To Windows Partition (NTFS), It Never Let Me Do That. How Can I Enable Read / Write Permissions In KUBUNTU 6.10? Please Help Me Guys With This One.:confused:

---

### Post by xopher on 2007-02-18
This is experimental, and might even be dangerous, so beware.

There's a driver called ntfs-3g, that works pretty well for this purpose though. More information here: [https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g) and here [http://doc.gwos.org/index.php/Write_ntfs](http://doc.gwos.org/index.php/Write_ntfs)

---

### Post by 7mm on 2007-02-18
Thank You "xopher" For Your Reply. Will Work On Your Idea!:guitar:

---

### Post by pebo on 2007-02-18
[Here]("http://givre.cabspace.com/ntfs-config/") is a nice little tool for setting up ntfs write support painlessly. As Xopher says ntfs write support is experimental. A better solution is to set up a FAT32 partition where you can share files between windows and ubuntu.

---


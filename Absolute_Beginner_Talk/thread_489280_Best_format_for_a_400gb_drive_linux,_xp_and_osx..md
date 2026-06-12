---
title: "Best format for a 400gb drive? linux, xp and osx."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by grim1234 on 2007-07-01
I'm having problems with a 400gb fat drive that I need to swap data between osx, linux and xp. It takes a long time to munt the drive in osx.

I need rw access in all three operating systems. Is there a better format to use?

Thanks!

---

### Post by apjone on 2007-07-01
Yikkies , the fat format is not really to be used for over 2gb or 64 gb if it is fat32. Is it a newtwork share or tripple boot system?

---

### Post by dropshot on 2007-07-01
You can configure Linux to write on NTFS drives, but I don't know if you can do that in OSX...

---

### Post by grim1234 on 2007-07-01
It's a maxtor external disk (usb). can be partitioned with cfdisk, so any format is possible really.

The trick is finding something that works in all three operating systems. fat32 is not ideal i agree.

It's to be used to store office documents, music, backups and photos. no operating system data, but needs to be rw in all three systems.

I don't think osx supports ntfs in with rw, just read only, or that would be fine.

Any ideas which filesystem?

---

### Post by stmiller on 2007-07-01
I would say to format it with ext3. There are OS X and Windows drivers that can read/write ext3. OS X project is on sourceforge. 

Second option would be HFS+, formatted from OS X. Linux can read/write from unjournaled HFS+, and I believe there is software to let Windows read and write to this.

OS X can read NTFS, but cannot write to it.

Try using the program gparted to format. It's nice!

---

### Post by hardyn on 2007-07-01
i use fat32 for my 320gb disk...

I never have a file larger than 4gb, and it allows me to move my exteral to other machines without adding addtional software; if you are using this drive for backup, do you really want to use a possibly unstable driver to write to it?  fat32 or VFAT is pretty much as perfected as its going to get, and can be accessed by any machine anywhere.

---


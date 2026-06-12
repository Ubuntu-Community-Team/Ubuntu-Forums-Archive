---
title: "Setting write permissions on an NTFS partition"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by mohapi on 2006-01-15
Sorry for what might be an oft-repeated question. I've searched the forums but found no conclusive answer.

I set up a dual boot using NTFS for what I was to be a "shared" partition between Ubuntu and WinXP. 

Now I can't seem to change the permissions from read-only for Ubuntu. 

Must this "shared" area be FAT32? Or is this possible with NTFS? What is the mounting command for writing permissions on an NTFS partition?

Again, sorry if this is a dumb question.

---

### Post by Qrk on 2006-01-15
Linux doesn't support write to NTFS (well, it can, but its a bad idea)

Make your shared folder FAT32

---

### Post by mohapi on 2006-01-15
[QUOTE=Qrk]Linux doesn't support write to NTFS (well, it can, but its a bad idea)

Make your shared folder FAT32[/QUOTE]

Thanks. That's what I needed to know. Cheers! :cool:

---

### Post by Omnios on 2006-01-15
WIth a ntfs drive you can only read/ copy files from that drive, with Vfat can read and write files

 This is the Ubuntu wiki about mounting windows drives
[http://help.ubuntu.com/starterguide/C/ch05.html]("http://help.ubuntu.com/starterguide/C/ch05.html")

 This is a good article about how fstab works but the page seems to be down at the moment.
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---


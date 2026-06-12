---
title: "Partition size on a dual boot system???"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by rcamanda on 2005-10-11
I have a dell Laptop inspiron 8600 with 40gb.  I want to evenly divide the drive.  When Prompted should I use 50%?  How do I split the hard drive in half?  I want a equal amount for windows an ubuntu.

Please help:)

---

### Post by aysiu on 2005-10-11
Is your Windows XP, 2000, or NT? If so, you may want to allocate a FAT32 partition to share files between Windows and Ubuntu.

[http://www.psychocats.net/essays/linuxguide.php#partitioning](http://www.psychocats.net/essays/linuxguide.php#partitioning)

---

### Post by rcamanda on 2005-10-11
[QUOTE=aysiu]Is your Windows XP, 2000, or NT? If so, you may want to allocate a FAT32 partition to share files between Windows and Ubuntu.

[http://www.psychocats.net/essays/linuxguide.php#partitioning](http://www.psychocats.net/essays/linuxguide.php#partitioning)[/QUOTE]


So ubuntu works with fat32?  How do I set that up?  Will the install prompt me?

---

### Post by aysiu on 2005-10-11
[QUOTE=rcamanda]So ubuntu works with fat32?[/quote] Please read what I linked to.

> How do I set that up?  Will the install prompt me? Yes, but you have to select "Manually edit partition tables" during install.

---

### Post by rcamanda on 2005-10-11
[QUOTE=aysiu]Please read what I linked to.

 Yes, but you have to select "Manually edit partition tables" during install.[/QUOTE]


Well before I read your post I reinstalled windows. C: with 19077mb and D with 19077mb. So when I do the install of ubuntu it should use D:    It will ask, if i remember right?  and it adds ext3 and swap I believe?

---

### Post by darkmatter on 2005-10-11
[QUOTE=rcamanda]Well before I read your post I reinstalled windows. C: with 19077mb and D with 19077mb. So when I do the install of ubuntu it should use D:    It will ask, if i remember right?  and it adds ext3 and swap I believe?[/QUOTE]

Ubuntu will ask, using the *nix designations, which drive to use, and will display the partition table for your approval before committing the changes.

Yes. The default partitioning will create / using ext3 as a standard partition and a swap partition using a logical drive.

---


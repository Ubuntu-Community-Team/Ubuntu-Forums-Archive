---
title: "ext3 vs fat32"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-08
as I've said before I want to install winxp with ubuntu
and the share partition could be fat32 or ext3
ext3 how ? - I've found a site (or shell I say YOU found it :) )
that make it possible to read and write to ext3 from xp

so the only question I have - wich is a better format ext3/2 (cuz winxp will read it as ext2 not ext3) or fat32 ?
wich is more realaible in winxp ?
has anyone used it before on xp ?

---

### Post by mostwanted on 2006-06-08
Just to be on th safe side, I'd use FAT. But why exactly do you want to make a new partition? Ubuntu can mount NTFS for reading and FAT for writing, so you'll be able to access all your files from there. Windows can, apparently access Ext3 with some unofficial drivers, so it should be able to access your Ubuntu files as well.

---

### Post by MaximB on 2006-06-08
ubuntu and every linux can read NTFS BUT cannot write to it
I need a shared folder...but fat32 cannot write/read files bigger then 4 gb
how about ext2/3 ?
is it safe for winxp ?

---

### Post by bruce89 on 2006-06-08
Don't use FAT as a /home directory, it would mess up all the permissions (or more the lack of them)

---

### Post by dvarsam on 2006-06-08
Hello!

FAT32 also has a size limit of 30GB (approximately) when you create Partitions!

Regarding NTFS partitions, there is this company that claims that you can now "Write" to them too (from Linux)!

Check this out:

[http://www.ntfs-linux.com/](http://www.ntfs-linux.com/)

Of course you have to pay for the product, but at the same time it might worth it (if it really does what it promises) and since FAT32 has all these limitations...

---

### Post by bruce89 on 2006-06-08
Sounds a bit like FUSE, which they nicked.

---

### Post by MaximB on 2006-06-08
yes I found this site before and posted about it in the forum - it isn't a new thing BUT the guys in the forum say it's not relaible YET and could couse problems
FAT32 have a limitation of 128GB per partition like it's been said here :
[https://wiki.ubuntu.com/LinuxFilesystemsExplained](https://wiki.ubuntu.com/LinuxFilesystemsExplained)
in the other hand FAT16 have a limitation of 2GB per partition.
and ext2/3 have a 4TB limitation per partition and 2TB per file.

I thing i'll take a risc and make the home partition ext3 and with the right driver I could read/write to it in winxp.

BTW
is there ANY program that could convert NTFS to ext3 without loosing data ?

---

### Post by kaamos on 2006-06-08
> FAT32 have a limitation of 128GB

Yep, but the thing that REALLY sucks is that the maximum file size is 4gb.

- A happy owner of a 160gb external drive formatted to ext3 8-)

---


---
title: "question about possible partitions"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-07-31
I was reading this page: [http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

and I noticed the one where you can create an NTFS for Windows and Ext3 for Ubuntu and not have to worry about the FAT32 partition because of a program called FS-Drive. But a side effect is that your /home partition would also have the shared files.

Is there a way to use this setup (i.e. no FAT32 partition) but still keep your /home partition separate from everything else, including the shared files? Or would creating a separate partition for the shared files necessarily entail a FAT32 partition anyway?

What does everyone think of this alternative of using FS-Drive instead of having a FAT32 partition?

Thanks,
John

P.S. Let me stick in another question here: using the default installation option with Dapper (i.e. letting it do the partitioning itself), does this mean I have no control over how big I can make the partitions? Does this give me a choice of creating the FAT32 partition for file sharing? Or do I have to use the manual option for these things?

---

### Post by aysiu on 2006-07-31
You could create three partitions, NTFS for Windows, Ext3 (for shared files), Ext3 for Ubuntu.

---

### Post by Paerez on 2006-07-31
You need to use the manual option to make your own fat32 partitions for sharing.

My opinion on FS-Drive: Yeah it's cool, but that means that if windows messes up, it could break ubuntu. Windows has no sense of linux file permissions in it, so you can't protect stuff from FS-Drive. I would go with a fat32 partition for sharing because it means windows won't take linux down if it has trouble with the fs-drive program or virus or whatever. Just from a safety standpoint.

EDIT: Aysiu's idea is better than fs-drive sharing the root and having a fat32, I would do that.

---


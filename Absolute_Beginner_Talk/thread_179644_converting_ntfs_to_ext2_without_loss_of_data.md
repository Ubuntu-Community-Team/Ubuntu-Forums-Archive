---
title: "converting ntfs to ext2 without loss of data?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by perolof on 2006-05-20
.... Is that possible? 
As you see Im new to linux, but I can say first taste, tastes good. My problem now is I have a 200gig drive full of music and pictures etc and I can mount and read that disk fine, but read only is not enough, I would like to be able to write too.
If I would have another empty ~200 gig disk I guess I culd format that one to ext2 and copy all data there, but I havent so what du you suggest I do?

---

### Post by Ubuntuud on 2006-05-20
Well, it isn't possible to format without loss of data. So do you know someone with a large external drive who might be a help to you?

---

### Post by skippy81 on 2006-05-20
Partition Magic is capable to converting NTFS to FAT32, but it costs money.  Also I wouldn't want to do such an operation without backing up first, and if you can backup then theres no point of converting.  

It is possible to read and write NTFS with ubuntu, check the forums,  Again there is risk involved.

The only safe thing to do is to backup the data.

---

### Post by adamkane on 2006-05-20
Moving your data to a new disk is the best option.

Your  biggest issue will be losing the special characters from your filenames:
[http://www.ubuntuforums.org/showthread.php?t=144297](http://www.ubuntuforums.org/showthread.php?t=144297)

---

### Post by scooper on 2006-05-20
NTFS can only be (somewhat) safely mucked with from Windows or a MS-sanctioned tool like Partition Magic that had access to Windows internals.  I would definitely do it as a copy operation.  Even if you have to copy twice to get it back on the original disk, it's simpler and far safer.

---

### Post by adamkane on 2006-05-20
!

---


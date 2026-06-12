---
title: "Windows share permissions"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by soutSA on 2006-08-15
Hello,

Hope somebody can help me with this, probably something easy. I am trying to connect to a windows share using the following as in thread [http://www.ubuntuforums.org/showthread.php?t=236564](http://www.ubuntuforums.org/showthread.php?t=236564) and adding it to my fstab

//192.168.1.5/New\Folder /mnt/windows cifs username=username,password=xxx 0 0

I am getting the following output:

[HTML]mount: block device //192.168.1.5/New\Folder is write-protected, mounting read-only
mount: cannot mount block device //192.168.1.5/New\Folder read-only
[/HTML]

:-k 
What am I doing wrong or what am I not doing at all. Can anyone please give some advice.

Thanks in advance

---

### Post by Iowan on 2006-08-15
Is it set up read-only on the Windows box?
(the backslash in the path looks odd, but...)

---


---
title: "Windows Files"
date: 2005-09-14
forum: Apple PPC Users
---

### Post by jam1n on 2005-09-14
I have yet to install the Ubuntu OS on my computer but i have used the Live CD.  I was very impressed and it seems good from what i have looked into regarding linux before. My question was If i install Ubuntu side by side with windows will i be able to access my windows folders while in Ubuntu or maybe just one folder because i know that in some versions of linux this is possible. thanks

---

### Post by mlomker on 2005-09-14
Yes, it can be mounted and generally will automatically be set up when you install.

---

### Post by beansbbq on 2005-10-02
[QUOTE=jam1n]I have yet to install the Ubuntu OS on my computer but i have used the Live CD.  I was very impressed and it seems good from what i have looked into regarding linux before. My question was If i install Ubuntu side by side with windows will i be able to access my windows folders while in Ubuntu or maybe just one folder because i know that in some versions of linux this is possible. thanks[/QUOTE]

The last I heard, you may be playing with fire if you attempt to write to Windows NTFS file systems, ie make changes to files on the Windows folder.  If you are looking at reading the files only, then you should be fine, e.g. playing an mp3s from the Windows folder.   

The Fat32 file system does not have this limitation.  You are free to read and write files on this file system.  Check into it before you pull the trigger.

---

### Post by stuporglue on 2005-10-02
If you're wanting to transfer files between Windows and Linux and your Windows is NTFS, your best bet is to make a small partition for this purpose and make it FAT32 so both can easily read it. You'll need to do this in the partitioner during the Ubuntu install, but it's the safest way.

---


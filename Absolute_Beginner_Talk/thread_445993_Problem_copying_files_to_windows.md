---
title: "Problem copying files to windows"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by pockets on 2007-05-16
Hi, I'm pretty new at this and...
I've got Ubuntu and Windows installed on my laptop. When I try to copy files from Ubuntu to Windows it says that I don't have permission to write there. If I right-click on it and try to change permissions it says I'm not the owner so can't change the permissions. 
Any help much appreciated - Thanks!

---

### Post by taurus on 2007-05-16
If your Windows is an ntfs filesystem, then you need to install ntfs-3g driver and use it instead of the default ntfs if you want to write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Terl on 2007-05-16
Using synaptic search for ntfs3g.  Install ntfs3g and the configuration tool (it is near the main ntfs3g entry, I forgot the exact name.  I am at work).  When doen you will have a configuration utility in your applications, system tools.  Run it and follow the instructions.  Remember to give write permissions too.

---

### Post by jputman01 on 2007-05-16
if you havent done it already you will need to get support for writing to NTFS, assuming you are using feisty here is some info and instructions

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by taurus on 2007-05-16
> **Terl said:**
> Using synaptic search for ntfs3g.  Install ntfs3g and the configuration tool (it is near the main ntfs3g entry, I forgot the exact name.  I am at work).  When doen you will have a configuration utility in your applications, system tools.  Run it and follow the instructions.  Remember to give write permissions too.

It's called ntfs-config.

---

### Post by pockets on 2007-05-16
excellent, I'll give it a go abd let you know how it works out...

---

### Post by Terl on 2007-05-16
> **taurus said:**
> It's called ntfs-config.

Thanks!  I thought so but was not positive.  One of the hindrances of forum posting from work :)

---

### Post by pockets on 2007-05-16
Thanks a million! Worked no problems.

---


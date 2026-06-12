---
title: "Live CD and NTFS"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Sonofmoog on 2007-05-24
Hello, after a couple hours browsing this site, and googling, I've learned that ntfs-3g can be downloaded and installed after a hard drive install.  

Which is great because safe, reliable read-write NTFS file access is something I must have.  I am assuming then that ntfs-3g does not come with the 7.04 LiveCD.  Is this correct?  Or, is there a way to use the LiveCD as a RescueCD for my NTFS volumes?

TIA

---

### Post by Happy_Man on 2007-05-24
Hmmm.... check the CD repos that you can access from Synaptic while booted into a live session, and see if it has the ntfs-3g package. If not, oh well. 

You _maybe_ could use the LiveCD as a Windows recovery CD, but then, nothing does windows recovery like   a REAL Windows recovery CD. Besides, ntfs-3g is absolutely safe; those who say it doesn't are either 

a) like the boy who cried wolf (eg spreading rumors) (or is that chicken little?)

b) don't know what they're talking about b/c they don't use it.

---

### Post by gn2 on 2007-05-24
> **Sonofmoog said:**
> Hello, after a couple hours browsing this site, and googling, I've learned that ntfs-3g can be downloaded and installed after a hard drive install.  

Which is great because safe, reliable read-write NTFS file access is something I must have.  I am assuming then that ntfs-3g does not come with the 7.04 LiveCD.  Is this correct?  Or, is there a way to use the LiveCD as a RescueCD for my NTFS volumes?

TIA

The Live CD should give read access to the NTFS partitions by default.

After installing a very easy way to make NTFS partitions auto-mount as writeable, is with the NTFS (and Fat32) auto-mounter that's available through [www.getautomatix.com](www.getautomatix.com)
[http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks#Miscellaneous_2](http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks#Miscellaneous_2)

---

### Post by staf4t5 on 2007-05-24
Check this link:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Sonofmoog on 2007-05-26
Thanks for the replies, folks.  I appreciate the help.  I think read-write NTFS file access makes all Linux LiveCD's into viable rescue disks for any Windows system.  I really hope the Ubuntu developers feel the same way ..

---


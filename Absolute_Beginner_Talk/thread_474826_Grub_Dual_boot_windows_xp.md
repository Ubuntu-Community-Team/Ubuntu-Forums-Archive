---
title: "Grub Dual boot windows xp"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Lotekx on 2007-06-15
Hi, I have been running ubuntu on my laptop, and recently decided to install windows. I can't get grub to recognize my windows installation though. here is my info...

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10326    82943563+  83  Linux
/dev/sda2   *       10327       11661    10723387+   7  HPFS/NTFS
/dev/sda3           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris
```


Any tips? thanks!

---

### Post by candtalan on 2007-06-15
when you install windows it overwrites the master boot record (MBR) on the active hard drive. Linux bootloadere (Grub usually?) would need to be in the mbr also, sio it can take over and the n handle windws too.

I think you will probably need to 'reinstall grub' or similar. It is a simple procedure but as a very newcomer Imust say it seenmeda bit complicated. However, I followed the instructions one by one and it worked easily.

this should do what you need I think:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by gentlemanmasher on 2007-06-15
This is also the method I use when reinstalling windows to get grub back.  Works very good.  What's strange is I have never had to reinstall my ubuntu.  Just another reason to love Ubuntu.

Funny how that works.

---

### Post by NJC on 2007-06-15
Forum member confused57 posted this Dual Boot link:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Specifically the Grub section is handy too:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---


---
title: "Replace Debian with Ubuntu"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by osprey101 on 2007-08-02
How do I remove Debian so that I can replace it with Ubuntu?
I have GRUB installed so that I can boot to Debian or Windows XP.

---

### Post by Kingsley on 2007-08-02
Format the Debian partition and install Ubuntu over it.

---

### Post by osprey101 on 2007-08-02
Can you give me more detail on formating partitions?
I think Debian has a few partitions.

---

### Post by sdowney717 on 2007-08-02
you could simply go into XP,
control panel administrative tools storage or something

and get to disk management.

Then click on any and all the debian partitions and remove them.

Make sure you have an ubuntu setup disk ready because if you do this you wont be able to boot the computer since it messes up grub. But this is ok since if you boot the live cd for ubuntu, and then install ubuntu to the free space it will fix everything.

If you want to get rid of the grub bootloader, boot the XP setup and get to the command prompt, recovery console, then type FIXMBR and it will just boot windows.

---

### Post by osprey101 on 2007-08-03
Thanks for your help. 
Interesting that you can access LINUX partitions in Windows Disk Management.
I had to boot Recovery Console and type FIXMBR to get the UBUNTU CD to boot.

---

### Post by xdarkxanarchyx on 2007-08-03
You can just use the Ubuntu LiveCD and use Gparted to format those paritions then install. It should automatically rewrite Grub. Or you can just begin the installation and make sure you click "format" for the parition(s).
Obviously the ones that are Ext3 are Linux and NTFS or FAT are Windows.

---


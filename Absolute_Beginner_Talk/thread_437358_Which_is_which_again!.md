---
title: "Which is which again?!"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2007-05-08
So, I have three hard disks - one **internal** (**40GB**) and two **external** (**250** and **400GB**).

GRUB labels them **sda**, **sdb **and **sdc**.

For booting I need to know which is which; since I have Linux installed to the **250GB** **external **one
Sometimes at boot time GRUB thinks the **250GB** **external **is **sdb **and sometimes it's **sdc**.

Is there any way to get GRUB to recognise my drives by some other identifier, such as a file or the drive's name?

Cheers in advance.

Edit: PS. My device map is:
[I](fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb[/I]

---

### Post by gradedcheese on 2007-05-09
For ext2 and ext3 file systems, you can use the "e2label" program to assign labels to the partitions, and then those can be used instead of names.  For example:

```

e2label /dev/sdb1 /

```

Would label sdb1 as '/' (a typical label for 'root' partition).  You can't use this on swap partitions, for swap you do:

```

sudo swapoff /dev/sdb0
sudo mkswap -L label_here /dev/sdb0
sudo swapon /dev/sdb0

```

(assuming sdb0 was the swap partition).  

You can also look at the disks this way, if you are curious:

```

ls -l /dev/disk/by-id/

```

This shows you some manufacturer name, linked to the device node (dev/sdb1 or whatever).

---

### Post by djheadley on 2007-05-09
Before I first installed Ubuntu, I wrote down the sizes of all my partitions and then mapped out what they would be called in Windows.  Then when I installed Ubuntu, I "named" the partitions that way, ie /win/c, /win/d, etc with /win telling me that they were Windows drives (fat32).  I still have it set up that way so I don't mess up and lose a file on a linux partition when I am going to have to get at it from Windows.  If I'm ever able to totally get away from Windows, then I'll change but for now, it works.  

BTW, I dual boot with Windows because I exchange files with my church (overhead projection, picture files, etc), and family.

---


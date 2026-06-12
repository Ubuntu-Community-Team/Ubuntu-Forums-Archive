---
title: "permissions for a slave harddrive"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by guddr on 2007-06-18
Hello,  I just recently installed Ubuntu 7.04 on a 80 gb hard drive and all seems to be working well.  However, I also have a 30 gb hard rive on the same computer as a slave and cant seem to add video clips to it.  A message indicates I need permissions and do not have them.  How do I go through root and basically give myself permission to work with that hard drive?  Thanks.

---

### Post by dreadlord_chris on 2007-06-18
> **guddr said:**
> Hello,  I just recently installed Ubuntu 7.04 on a 80 gb hard drive and all seems to be working well.  However, I also have a 30 gb hard rive on the same computer as a slave and cant seem to add video clips to it.  A message indicates I need permissions and do not have them.  How do I go through root and basically give myself permission to work with that hard drive?  Thanks.

How is the 30GBer formated?

---

### Post by guddr on 2007-06-18
It was formatted using Windows XP.

---

### Post by dreadlord_chris on 2007-06-18
> **guddr said:**
> It was formatted using Windows XP.

so it's probably formatted NTFS. Are you dual-booting XP & Ubuntu, and want the drive accessible to both? If so then you need to install ntfs-3g
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

If you're not dual-booting - is the drive empty? If so, use **gparted** to reformat it ext3 - gparted is in the repositories:
```

sudo apt-get install gparted

```
If you reformat you will need to edit **/etc/fstab** to reflect the new format (just change ntfs to ext3)
```

sudo nano /etc/fstab

```

---


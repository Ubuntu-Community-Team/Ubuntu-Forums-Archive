---
title: "Can't access Ubuntu Partition"
date: 2008-10-11
forum: Apple Hardware Users
---

### Post by gamgee911 on 2008-10-11
Hey Guys,

I just installed Ubuntu over my Vista Partition on my MacBook Pro.  I did this by booting on the live disk, deleting the dev/sda3 partition and reformating it to in ext3 and installing ubuntu.  When I rebooted the computer holding down option I only get the Mac boot option, no option for windows/ubuntu. Anyone know how to get Boot Camp to see my linux partition?  Thank you!

---

### Post by cyberdork33 on 2008-10-12
> **gamgee911 said:**
> Hey Guys,

I just installed Ubuntu over my Vista Partition on my MacBook Pro.  I did this by booting on the live disk, deleting the dev/sda3 partition and reformating it to in ext3 and installing ubuntu.  When I rebooted the computer holding down option I only get the Mac boot option, no option for windows/ubuntu. Anyone know how to get Boot Camp to see my linux partition?  Thank you!
see this thread:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

I think you need to install grub again as is shown in the last part of the post.

---

### Post by gamgee911 on 2008-10-12
thanks, I ended up having to install rEFIt and it works fine now.  now I'm trying to figure out if I can boot my ubuntu parition in mac os x via vmware and vice versa.

---


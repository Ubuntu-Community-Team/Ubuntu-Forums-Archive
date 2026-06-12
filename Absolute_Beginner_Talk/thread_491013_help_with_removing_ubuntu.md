---
title: "help with removing ubuntu"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by cmagan on 2007-07-03
i have dual boot and i want to stay with windows only for a while.
is there any guide that explains how to uninstall ubuntu?
is it easy as installing it?

---

### Post by jordanmthomas on 2007-07-03
You can just use your Windows CD, boot to a recovery console and type
```
FIXMBR
```
Tell it you want to overwrite the MBR and Ubuntu is (logically anyway) gone.

After that, you can use Gparted on the LiveCD or the Disk Management Tool in Windows to reclaim the partition(s) you used for Ubuntu.

A quick search on Google gave this:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu](http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu)

---


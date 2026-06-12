---
title: "How to completely remove"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by ubuntmetu on 2006-08-31
I have tried various Linux distributions before, and many times I have run into the same problem, un-installing it. There always seems to be a problem with some piece of hardware that can not be resolved, and then there is GRUB.
I can’t get GRUB un-installed so I find a way to leave it in, and be annoyed with the bootup selection until finally formatting my HDD and so on…
Is this distribution the same way? If I don’t like it or care not to keep it will I have problems removing it?
I do want to find something other than “Windows”, and its bloated software, to use and hopefully will not have to un-install ubuntu.
I have tried the LIVE unbuntu, and there were no problems. every thing I tried seemed to work.

---

### Post by jordanmthomas on 2006-08-31
To remove grub (and replace it with Windows' boot loader), boot off a Windows install CD and tell it you want to repair an installation.  Once you're logged in (it will be on a command line) you'll need to type FIXMBR.  This will get rid of Grub.  Getting rid of the partitions can then be done in Windows.

(Of course, I was assuming you had Windows installed)

Also, if you install another Linux instead of Windows, you can usually run grub-setup to make yourself a nice new Grub.

---


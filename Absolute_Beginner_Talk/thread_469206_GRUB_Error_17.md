---
title: "GRUB Error 17"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by browserjoe on 2007-06-09
Okay, so I have a 250GB HD with XP using 210GB and Ubuntu 7.04 using 40GB.  

Ubuntu was being a bitch with installing programs and updates and I locked myself out of admin privalages.  So I decided to reinstall the OS.

I selected the HD partition Ubuntu was previously on, everything installed fine until 94% when an error came up saying "GRUB failed to install, this is a fatal error"

So I try it again, same thing happens.  

Then I reboot my computer and the error says:

> Grub loading, stage 1.5

GRUB failed to load
Error 17


And then it does nothing. 

How do I get back to XP?  Will burning a new Ubuntu CD work and installing ubuntu agian work?

I think it was because GRUB was installed on the Ubuntu partition which I deleted and when I tried to reinstall it something screwed up...

---

### Post by benerivo on 2007-06-09
You're right in thinking that it's broken because grub was in the Ubuntu partition you partially wrote over during the reinstall. You will need to reinstall some sort of boot loader. Putting Ubuntu back on would have been perfect should it have worked. If you have the windows cd's you can install that on the 40GB partition and it will install the windows boot loader, which will give you a boot option for XP on the 250GB partition. The only other way would be to install any linux on the 40GB. If I were you I would try Ubuntu again, but use gparted from the live cd's main menu to delete the 40GB partition and use the free space to create an ext3 formatted /boot partition and a ext3 / (root) partition, so that deleting a broken linux OS does not remove the boot loader from the system.

---


---
title: "Used fixmbr, now rEFIT doesn't see Ubuntu partition"
date: 2010-04-05
forum: Apple Hardware Users
---

### Post by alan4cult on 2010-04-05
Hi,

I have 3 operating systems on my Macbook: Ubuntu 9.10, OS Snow Leopard and Windows Xp. I use rEFIt as my boot menu. When i used to select the Windows Partition it would load Grub and then I would have to choose Windows from the grub menu again. I found this annoying so I booted windows from cd and used the fixmbr command to fix this. But now rEFIt no longer sees my Ubuntu partition. How can I correct this?

---

### Post by linuxopjemac on 2010-04-05
You could start by syncing the partition table. You can do this from within rEFIt. I do think you need to install Grub again. You can do that if my 1st idea does not work:

[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---


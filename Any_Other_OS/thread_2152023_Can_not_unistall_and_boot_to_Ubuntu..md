---
title: "Can not unistall and boot to Ubuntu."
date: 2013-06-06
forum: Any Other OS
---

### Post by TheHermes on 2013-06-06
Hello, few months ago I have encountered a problem. Currently I am running Windows XP alongside with Linux Ubuntu 12.10. The issue I am having is that I just can not boot my PC to Ubuntu OS, because the menu where you choose OS you want to boot is missing. Since I did not have something important in my Ubuntu file system I decided to unistal it in Windows add remove programs menu, but no luck. I receive error message and a log with the cause of the problem. Its is really important for me to remove Ubuntu because after the issues with it for some reason my C: drive is always almost full even though I removed all non crucial programs and files from it. I believe it has something to do with this problem of Ubuntu not booting up. I will provide my error log, maybe that way someone will be able to help me. Side fact, also very interestingly my C: partition in Windows shows double the physical memory it actually has. It started showing double amount of physical memory when I installed the Linux Ubuntu. Thank you in advance. Error log download link: [https://docs.google.com/file/d/0BzhA2hfQWq1jSXduUDNJUzY5TG8/edit?usp=sharing](https://docs.google.com/file/d/0BzhA2hfQWq1jSXduUDNJUzY5TG8/edit?usp=sharing)[RIGHT]Your sincerely, 
David
[/RIGHT]

---

### Post by M1773N5 on 2013-06-06
you can remove ubuntu through windows using the disk utility. Click start> right click my computer and select manage. Click the disk management icon and locate the partition you installed ubuntu on. You can then delete it and use the new unallocated space to extend your C:\ drive.

---

### Post by TheHermes on 2013-06-06
The problem is that Ubuntu is installed in my C: drive, so I will not be able to delete my system partition and expand for more memory. What else should I do?

---

### Post by TheHermes on 2013-06-06
a

---

### Post by TheHermes on 2013-06-06
The problem is that Ubuntu is installed in my C: drive, so I will not be  able to delete my system partition and expand for more memory. What  else should I do?

---

### Post by oldfred on 2013-06-06
That is a wubi install which is just a large file system inside the NTFS Windows partition.

Both links have further info on uninstalling.
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can manually delete the root.disk file and edit the boot.ini to remove the ubuntu entry. Back up data in Ubuntu first if you have anything you want to save.

---


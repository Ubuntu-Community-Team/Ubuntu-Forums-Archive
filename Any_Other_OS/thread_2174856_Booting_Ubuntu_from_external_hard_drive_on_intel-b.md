---
title: "Booting Ubuntu from external hard drive on intel-based MacBook Pro"
date: 2013-09-16
forum: Any Other OS
---

### Post by CheshireMD on 2013-09-16
[INDENT]Good day everyone. 

 
I  have MacBook Pro(late 2011) with OS X 10.7.5 and external hard drive  with Ubuntu 13.04, from wich i can boot succefully on my PC. But MacBook  Pro will not boot from my external drive, no matter which  key/combination i use during restart.
 
After googling I found some answers to my initial question, how to boot from external hard drive
 
[https://discussions.apple.com/thread/1852633?start=0&tstart=0](https://discussions.apple.com/thread/1852633?start=0&tstart=0)
 
[http://www.everymac.com/systems/apple/macbook_pro/faq/macbook-pro-boot-from-exte rnal-firewire-or-usb-drive.html]("http://www.everymac.com/systems/apple/macbook_pro/faq/macbook-pro-boot-from-external-firewire-or-usb-drive.html")
 
[http://support.apple.com/kb/ht1948](http://support.apple.com/kb/ht1948)
 
[B]As  I understand I need to format my external hard drive into GUID  partition type, reinstall ubuntu and this will be enough to be able to boot from it on my  mac?
[/B]
[B]With this new partition type, will I be able to install ubuntu again on my external drive?
[/B]
[B]Does  GUID partition type supports NTFS, ext4 and FAT32, linux swap?
[/B]
**Will I be able to boot from my pc from my external drive with this new partition type?**
**What are downsides, if any, to GPT?**

P.S. I already raised same question in apple community, about a week ago, but seems like no one know the answer to my questions there. Since then, I looked for info on GUID on internet
[http://support.microsoft.com/kb/302873](http://support.microsoft.com/kb/302873)
[http://www.uefi.org/learning_center/](http://www.uefi.org/learning_center/)
 and did not found any answers to my questions. If you can point me where to look for info, i would appreciate it also.

[/INDENT]

---

### Post by UltimateCat on 2013-09-26
Hi:

I think the only time you have to perform gpt partitioning is if your external HDD is 2.2 or larger. Because of the RAM--

> [B]With this new partition type, will I be able to install ubuntu again on my external drive?
[/B]
**Does  GUID partition type supports NTFS, ext4 and FAT32, linux swap?**


You should be able to install Ubuntu on the exernal yes.
I don't know if GUID partitioning supports NTFS--
But I'm pretty sure it supports Linux:-
[https://wiki.archlinux.org/index.php/GUID_Partition_Table](https://wiki.archlinux.org/index.php/GUID_Partition_Table)

By default at least for Mac/BSD) gpt creates a table supporting up to 128 partitions-
[http://superuser.com/questions/226983/guid-partition-table-linux](http://superuser.com/questions/226983/guid-partition-table-linux)

As long as you can tell your Mac to boot to the usb drive first you will be able to use that external HDD-

You could dual boot your Mac with Ubuntu but I am still learning and don't know Mac commands yet- Sorry
Hope this helps-

---

### Post by CheshireMD on 2013-09-27
thanks a lot for the links! archlinux.org was really helpful.

about commands for mac. you can find them here

[http://support.apple.com/kb/ht1533?viewlocale=en=en](http://support.apple.com/kb/ht1533?viewlocale=en=en)

---

### Post by UltimateCat on 2013-09-27
Your very Welcome- [**[COLOR=#000000]CheshireMD[/COLOR]**]("http://ubuntuforums.org/member.php?u=1292922")

And thank you for the link to Mac commands!

---


---
title: "ubuntu installation on Apple, not on the main disk"
date: 2010-05-11
forum: Apple Hardware Users
---

### Post by hanat on 2010-05-11
I have a super computer, with 16GB RAM, and 4*1TB hard disks, before there is only Mac 10.5.8 Leopard installed, and 2 hard disk were used, and other 2 were used as mirror for the used disk using RAID system.

Now since i need to install unbuntu on my mac, i used the hbc/sda for mac, and hbc/sdb for Ubuntu, and rest two for Data only. I installed rEFIt, and run the Ubuntu Desktop version 10.4 CD for installation,
I choose hbc/sdb for installation of Ubuntu, and format a big chunk as ext3, and rest as swap(actually i dont know how much disk space should i left for swap, i used 50GB,and rest 950GB as ext3 Filesystem).
and in the grub installation option, i dont know where should i install it, as i read in this forum, i should install it on hbc/sda, however i am installing ubuntu on my hbc/sdb, i dont know where i should put the grub.

i dont know if anyone had experiences in this kind of situation, really look forward for some helps.

---


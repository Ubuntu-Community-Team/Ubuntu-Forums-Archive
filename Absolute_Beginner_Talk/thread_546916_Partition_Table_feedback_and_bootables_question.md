---
title: "Partition Table feedback and bootables question"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by glarnewbie on 2007-09-09
Hello all!  After reading up on the advantages of strategic partitioning, I've successfully installed 6.06 LTS server with a partition table I think should work for me.  I plan on using this computer as a proxy server mostly.  I based my setup on the information found on the following websites:
[http://www.faqs.org/docs/Linux-mini/Partition.html](http://www.faqs.org/docs/Linux-mini/Partition.html)
[http://www.linuxclues.com/articles/01.htm](http://www.linuxclues.com/articles/01.htm)
[http://margo.student.utwente.nl/simon/ongoing/linuxpart.php](http://margo.student.utwente.nl/simon/ongoing/linuxpart.php)

I was hoping to get some feedback on the setup?  Here it is:
/dev/hda1  Primary  /boot  600MB  Ext3  Default Mount Options  No label  Standard Use  Bootable Flag On
/dev/hda2  Primary  /         600MB  Ext3  Default Mount opts       No label  Standard          Bootable Off
/dev/hda3  Primary  /usr      2 GB    "                                                                                                        "
/dev/hda4  Logical   Swap  500MB   "                                                                                                        "
/dev/hda5  Logical  /Home    2 GB    "                                                                                                        "
/dev/hda6  Logical  /var/log  2 GB    "                                                                                                        "
/dev/hda7  Logical  /var     12.3GB  "                                                                                                        "

It was a pretty quick learning curve to setup this table through the installation Partitioning Section.  The only actual question I have at this point is about the "bootables."  Should all partitions be flagged "On" or just the /boot partition?

Any help is greatly appreciated!

---

### Post by meindian523 on 2007-09-09
I believe only the / and /boot partition should have bootable flags coz they are the ones which contain the Grub files.

---


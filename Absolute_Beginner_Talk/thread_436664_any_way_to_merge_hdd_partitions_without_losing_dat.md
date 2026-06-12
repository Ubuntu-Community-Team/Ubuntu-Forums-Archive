---
title: "any way to merge hdd partitions without losing data?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by basebALLSTAR3012 on 2007-05-08
Hi, I was planning on upgrading to Ubuntu and took the preliminary steps of partitioning my hdd. However, I simply need all the space on this machine possible for my windows apps and unfortunately can't use Ubuntu with this computer due to said space requirements. I want to know if it's possible to put the partition I had set aside for Ubuntu back into the main drive without losing all the data i have on the main partition. How does one do this? 
Thank you.

---

### Post by Bachstelze on 2007-05-08
I don't think I understand correctly what you want to do. Could you please describe more precisely how your drives are currently partitioned and what you would like to do ?

---

### Post by jiminycricket on 2007-05-08
Backup everything on the windows partition first (I like this tutorial for backups btw: [http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc) ) Defragment, chkdsk /r, etc.

Then boot up a live cd and use gparted to delete the ubuntu partition and resize the Windows partition to include it.  This might not work with  Vista though unless you use ntfsfix after.

---


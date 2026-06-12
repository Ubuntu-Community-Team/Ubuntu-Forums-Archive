---
title: "Fix Vista MBR?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-03-05
I installed Ubuntu 6.10 on a second SATA hard drive, and GRUB installed on my first Vista hard drive. Neither operating system will boot unless both hard drives are in, and I need to know how to repair the MBR for the Vista hard drive. 

Can anyone tell me how to do this?

---

### Post by nudnik on 2007-03-05
> **Shack_ said:**
> I installed Ubuntu 6.10 on a second SATA hard drive, and GRUB installed on my first Vista hard drive. Neither operating system will boot unless both hard drives are in, and I need to know how to repair the MBR for the Vista hard drive. 

Can anyone tell me how to do this?

Get into DOS one way or another and type: fixmbr. With luck the Vista install DVD allows you to do this as the XP install CD does.

---

### Post by Shack_ on 2007-03-05
Will I be able to boot Ubuntu after that? Or will I need to reinstall it? And how would I prevent this in the future?

---

### Post by oilchangeguy on 2007-03-05
i'm not sure how the vista dvd works. but with xp (if you have a true xp disc, not a factory restore disc) boot from the disc, when it loads select "R" to enter the repair console, at the command prompt type fixmbr, enter. you should get a confirmation that it's been completed, then reboot and see what happens. if your copy of vista came with a new computer this probably won't work. if you've got a retail version it should.

---

### Post by Shack_ on 2007-03-05
Vista was pre-installed, so if it doesn't work, would you have any suggestions?

---

### Post by dosmode on 2007-03-05
You may get some useful info here : [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---


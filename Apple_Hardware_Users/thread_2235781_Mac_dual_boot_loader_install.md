---
title: "Mac dual boot loader install"
date: 2014-07-22
forum: Apple Hardware Users
---

### Post by dylan27 on 2014-07-22
I have an iMac with a large mac partition, a small windows partition and -- now -- a medium Ubuntu 14.04 partition. Everything went fine with USB install using Mac Linux USB Loader until the end of the download. After I restarted with USB in and help down the alt/option key, I installed Ubuntu, but at the end it said that it could not install a boot loader and that this was necessary to be able to boot up the program.

I have rEFit installed, and I know to hold down the alt/option key on restart, but indeed Ubuntu could not be found. How would I go about manually installing a dual (or tri) boot loader for iMac 10.8.5?

Thanks in advance,

Dylan

---

### Post by yancek on 2014-07-22
Where did you try to install the bootloader?  The default is to the mbr of the primary drive.  Since you are using a different bootloader to boot your other systems, did you try to install the Grub bootloader to the partition on which you installed Ubuntu?  That has always worked for me but then, I've never used a Mac.  Anything more detailed in the message about not being able to install the bootloader?

---

### Post by QIII on 2014-07-22
Moved to Apple Users.

---


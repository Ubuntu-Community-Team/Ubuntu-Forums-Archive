---
title: "Cannot find operating system"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Tangerined on 2006-09-26
Hi, I just installed ubuntu on my system with a existing installation of windows xp. I installed ubuntu on its own hard drive, I just selected the hard drive in the installation and let the installation figure out the partitions itself. After the installation and when I tried to boot from the hard drive that I installed on, I get the message "Error Loading Operating system". And my windows still boots up fine.

Ok some extra info: 
I have 4 hard drives
250 sata - windows
250 sata
80 ide - master
160 ide - slave, ubuntu. 

when i try to boot from the 80gb hd i get this msg: Could not load grub, error 17.

---

### Post by kidders on 2006-09-26
Hi there,

It looks as though you may have decided to reorder your disk drives after installing Ubuntu. This isn't a terribly good idea, until you've figured out how to tell Linux you're planning to do that.

Your bootloader seems to be on the 80G IDE drive ... does that seem sensible to you?

Incidentally, "Error Loading Operating system" is probably a message from your BIOS to say that the disk you tried to boot from isn't bootable. It's quite normal.

---

### Post by gn2 on 2006-09-26
I would suggest you decide which drive you want to install Ubuntu on. Then disconnect all the other hard drives.
Then re-nstall Ubuntu and the bootloader on the chosen drive.(suggest IDE master)
Now re-connect all the hard drives.
At boot time, simply point the bios to the drive you want to boot from. (Using F8 or other key depending on make)
Once you're up and running like this you can configure Ubuntu's access to the other drives.

My reason for suggesting this method is to avoid potential difficulties with Ubuntu over-writing your Windows MBR...
(if it hasn't done so already)

---

### Post by Tangerined on 2006-09-27
Great thanks, I did what you said about unplugging all the other drives and did the install. Now it boots up fine.

---


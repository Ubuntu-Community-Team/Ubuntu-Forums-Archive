---
title: "New installation"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by JVS2118 on 2007-11-18
Hi all
I am new to Ubuntu.

I have 2 hard drives installed on my pc.

I use the one for Windows XP and the other as a slave. Nothing is installed.
I want to install Ubuntu on the 2nd hard drive.
How do i do it so that when i turn my machine on i get the option of which O/S so use.


Thanks

---

### Post by PmDematagoda on 2007-11-18
Ubuntu will install Grub automatically which will allow you to boot between both Windows and Ubuntu. All you need to do is specify in the Ubuntu installer that you want to install Ubuntu on the entire second HDD and give some extra information concerning username, etc. After that Ubuntu will do everything you need, no extra configuration required, especially for the boot-loader, just make sure that you are installing Ubuntu on the second HDD instead of the first one where Windows is located.

---

### Post by Skefflock on 2007-11-18
Just load from lifeCD, start the installation on the hard drive, and on the 2nd or 3rd page of installation config you'll see options of where to install, on what drive. And here's should be an option (assuming you have 2 drives installed and worked) to use the entire second drive for installation. It will be automatically reformatted and separated into Linux partitions. Everything on the second drive will be lost!

---

### Post by Skefflock on 2007-11-18
And yes, As PmDematagoda mentioned earlier, the Grub will me configured automatically so you will be able to choose between OS at startup.

---


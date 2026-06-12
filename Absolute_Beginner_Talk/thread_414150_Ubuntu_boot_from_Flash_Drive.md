---
title: "Ubuntu boot from Flash Drive"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by dmpolska on 2007-04-19
Hello all. I was wondering if there is anyway I can boot Ubuntu from a flash drive (I have a 2.0 Kingston thumb drive). I am working on a computer where the whole operating system is wiped out AND the cd/dvd drives do not work. Any help would be appreciated. 

Thank you

---

### Post by cypherzero on 2007-04-19
Yes, you can.

Similar to installing Ununtu to any external USB drive - providing your computer can boot from it.

Boot up the Live CD on a computer and simply tell the installer to install to the flash drive.

I had problems in getting GRUB to install to my external drive using the Ubuntu installer.
I had to let the installer install GRUB to my primary hard disk first, and then after all was set up I used Linux to install GRUB to my external drive. If you also have this problem you can always change your bootloader on your primary disk post-install.

---

### Post by Gazneth on 2007-04-19
Here is a link to set up a total Ubuntu install to a usb drive. This allows you to save data and install additional packages to the drive. [HTML]http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610[/HTML]

---

### Post by nhandler on 2007-04-19
I had the same problem. Here is the thread that I posted which contains the solution: [http://ubuntuforums.org/showthread.php?t=323117](http://ubuntuforums.org/showthread.php?t=323117)

I would recommend not doing this. It will shorten the life span of the flash drive, and it won't run as fast as if you were booting off the cd or the computer.

---


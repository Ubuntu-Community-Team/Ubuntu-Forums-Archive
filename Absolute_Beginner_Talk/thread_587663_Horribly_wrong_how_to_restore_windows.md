---
title: "Horribly wrong: how to restore windows"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by P373 on 2007-10-22
Hello;

I had been following all the instructions to make my laptop dual boot linux and windows (windows was already installed)...

Ubuntu is now installed and windows is completely gone. I have my drive image backed up on an external hard drive (backed up via Drive Image XML). How can I restore this image and all its data / windows OS so I can get all my things back?

Thank you for any efforts;

Peter.

---

### Post by Maestro23 on 2007-10-22
Are you sure the windows partiton is totally gone?

In a terminal type and post reslults of:

> sudo fdisk -l

Also what is in your menu.lst (lower case L)

cat /boot/grub/menu.lst

---


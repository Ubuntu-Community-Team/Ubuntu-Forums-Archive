---
title: "Yet Another Newbie Dual Boot Question"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by wintermute2_0 on 2006-09-18
My Windows installation is on my primary (C:) drive.  It's a FAT32 drive with about 17GB free.  I want to install Ubuntu on my slave drive (D:) and have GRUB on the mbr and boot to the slave drive when I select Ubuntu.  Is this possible without monkeying with jumpers and IDE cables?  Also, how much space should I allocate on my slave drive for Ubuntu?  I have about 80GB free.  Thanks so much for your help.

---

### Post by bulldog on 2006-09-18
If you have your drives correctly atached to your computer,there shouldn't be a problem.

GRUB on your primary hdd and then boot to UBuntu is no problem either.

The partitioning depends on what you wanna do.
Just boot and install nothing,needs less space instead off downloading lots of stuff and installing everything you see.

I can give you a little  guide though.

Do the partitioning by yourself not automatic.

Create a / [root] partition 10 GB
Create a swap 1 or 2 GB
Create a /home as big as you think you need.

---


---
title: "Partitions"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by mikeee52 on 2006-11-05
I installed Ubunto Edgy Eft 6.10 on one partition on my hard drive then went back and upgraded dapper drake to Edgy Eft. How do I delete Edgy Eft on the one partition, (not the upgrade) and get it off the Grub boot up menu. I will need instructions.

Thanks in advance
   mike

---

### Post by Kateikyoushi on 2006-11-05
I would recommend to use gparted.

To install it xopy this to terminal.
```
sudo aptitude install gparted
```

To start it.
```
sudo gparted
```

Right click on the partition you want to delete or reformat and select from the menu. If it is mounted have to unmount first.

Make a backup of your grub.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

This will open your grub menu for editing.
```
sudo nano /boot/grub/menu.lst
```

Delete or hash the options you do not use.

---


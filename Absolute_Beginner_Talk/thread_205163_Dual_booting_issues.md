---
title: "Dual booting issues"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by bruenig on 2006-06-28
I am dual booting ubuntu with microsoft Bob, i have dual booted before succesfully however ubuntu failed to recognize Microsoft Bob, I am wondering if anybody else has had these problems and how to get an option to boot into Microsoft Bob on grub.

---

### Post by oyvindaa on 2006-06-28
You have to open menu.lst in the grub folder, like this:

```

sudo gedit /boot/grub/menu.lst

```

Then you add an entry for Windows, at the end of the file.

[http://ubuntuforums.org/showthread.php?t=202489&highlight=add+windows+grub](http://ubuntuforums.org/showthread.php?t=202489&highlight=add+windows+grub)

[http://ubuntuforums.org/showthread.php?t=201368&highlight=add+windows+grub](http://ubuntuforums.org/showthread.php?t=201368&highlight=add+windows+grub)

[http://ubuntuforums.org/showthread.php?t=200518&highlight=add+windows+grub](http://ubuntuforums.org/showthread.php?t=200518&highlight=add+windows+grub)

Good luck.

---

### Post by aysiu on 2006-06-28
oyvindaa is basically right. A few things I would add, though:

1. Always back up any system file you're about to edit: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

2. Always use *gksudo* for graphical applications instead of using *sudo*: ```
gksudo gedit /boot/grub/menu.lst
``` For a full explanation of why, go here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

3. The entry should look something like this: ```
title           Microsoft Windows XP Home Edition
root            **(hd0,0)**
savedefault
makeactive
chainloader     +1
``` Assumes, of course, that Windows is on /dev/hda1. If it's really at /dev/hda2, it should be **(hd0,1)**. If it's on /dev/hdb1, it should be **(hd1,0)**. Numbering starts at 0, in case you couldn't tell.

If you have no idea where it lives, paste this command into the terminal and look for the appropriate NTFS or FAT32 partition: ```
sudo fdisk -l
```

---

### Post by oyvindaa on 2006-06-28
Thanks aysiu :)

---


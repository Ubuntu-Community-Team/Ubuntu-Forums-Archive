---
title: "Help, Big, Big Troubles"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2006-01-27
Ok I was doing a system backup and I ran out of disk space. Since it wasn’t going to be a full backup I closed the terminal and rebooted. Now I cannot log in. It says my disk is full! 

I got the backup instructions from the wiki page [https://wiki.ubuntu.com/BackupYourSystem?highlight=%28system%29%7C%28backup%29]("https://wiki.ubuntu.com/BackupYourSystem?highlight=%28system%29%7C%28backup%29")

How do I undo what was written to the drive for the backup?

How do I log back on to undo it?

Thanks
Bill

---

### Post by cotcot on 2006-01-27
Try to delete some files with the Ubuntu live CD.

---

### Post by az on 2006-01-27
If you do not have the live cd, you can always just use the install cd and use the rescue mode.

That will chroot you into a partition you chose.

You can also just delete files form the installer without chrooting

Boot the instaler
let it detect your hardware
then,
CTRL-ALT-F2
mkdir /mnt
mount /dev/hda1 /mnt
rm /mnt/backup/* (or whatever else you want)

---

### Post by Micro Rotors on 2006-01-27
Ok I fixed it before checking back. What I did was login safe mode terminal, then ls command, cd / = ls = rm -i backup.tgz   then I confirmed it and WAH-LA! its fixed!!!!

Thanks for the help anyways,,,, this place is GREAT!
Bill

---


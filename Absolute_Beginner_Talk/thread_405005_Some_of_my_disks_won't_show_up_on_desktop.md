---
title: "Some of my disks won't show up on desktop"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Iceni on 2007-04-09
.. or in file manager.

I manually edited the fstab file and got everything working the way I want it, and everything is actually mounted in /media/, but only 4 of 6 disks/partitions shows up in the file manager and on the desktop. Me being a newbie, I can't figure this out myself. Can anyone help me out?

fstab:
```
proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=a0f7594d-502b-494e-b1b5-041cafd4c921 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=40c75d2d-713e-408c-8f77-85eea121f861 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda2 /media/f248 ext3 defaults 0 0
/dev/sda1 /media/Serenity ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdc1 /media/Graendal ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdd1 /media/Habu ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdd2 /media/Ohabu ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sde1 /media/River ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

I set folder permissions manually with this command:
> sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage


Bonus question:
Can I edit device.map file (grub) manually and instert the data from fdisk -l or can this possibly break things?

Thanks in advance! :)

---

### Post by seshomaru samma on 2007-04-09
is your user name marie?

---

### Post by Iceni on 2007-04-09
> **seshomaru samma said:**
> is your user name marie?

No :)

---

### Post by games130 on 2007-04-09
have you got automatix2? i just installed it yesterday night and installed a software that read and write fat32 and ntfs drives. After the installation and restart i can see my ntfs drives no problem.

---

### Post by seshomaru samma on 2007-04-09
just to be on the safe side, you did use your own user name in this command:
sudo chown -R marie:marie /storage
right?

---

### Post by Iceni on 2007-04-09
> **seshomaru samma said:**
> just to be on the safe side, you did use your own user name in this command:
sudo chown -R marie:marie /storage
right?

Yes. I just posted the commands I found without editing in my own username. I can access (read/write) the hard drives just fine, they are mounted, but I would like them to appear on the desktop and in the file manager like the other ones. 

> have you got automatix2? i just installed it yesterday night and installed a software that read and write fat32 and ntfs drives. After the installation and restart i can see my ntfs drives no problem.

Thanks, but I don't think automatix is for feisty yet. I have ntfs-3g installed and working so that is not the problem.

---

### Post by vatechtigger on 2007-04-09
which ones don't show up?

---

### Post by Iceni on 2007-04-09
> **vatechtigger said:**
> which ones don't show up?

These:

/dev/sda2 /media/f248 ext3 defaults 0 0
/dev/sda1 /media/Serenity ntfs-3g defaults,locale=en_US.UTF-8 0 0

The first one is a partition and the 2nd one is a standalone disk.

---

### Post by vatechtigger on 2007-04-09
Take this with a grain of salt because Im very new to this, but is it possible that you dont have the labels right. 

It was my impression that each disk gets a different label, so that if /media/f248 was a different disk than serentity it couldn't be labeled sd**A** but would have to be sd**B** or however it shows up in gparted.

---

### Post by Iceni on 2007-04-09
> **vatechtigger said:**
> Take this with a grain of salt because Im very new to this, but is it possible that you dont have the labels right. 

It was my impression that each disk gets a different label, so that if /media/f248 was a different disk than serentity it couldn't be labeled sd**A** but would have to be sd**B** or however it shows up in gparted.

You are of course correct, I gave you wrong information. They are partitions of the same disk. The only IDE-drive in the computer, could that have anything to do with it?

---

### Post by vatechtigger on 2007-04-09
Ive had been having a bunch of trouble with my fstab and partitions as well. here is my thread.

[http://ubuntuforums.org/showthread.php?t=403975](http://ubuntuforums.org/showthread.php?t=403975)

deleting the UUID info and just labellng everything with /dev/sda, etc solved the problem. I don't
know why though but maybe worth a shot.

---

### Post by Iceni on 2007-04-09
Thanks, I'll read a bit:)

---


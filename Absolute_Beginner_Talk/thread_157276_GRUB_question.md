---
title: "GRUB question"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-04-08
I have a master hard drive with 40 GB, the first 10 GB of which using XP PRO (NTFS)
I have a secondary (slave) HD with 20 GB, the first 10 GB using XP PRO (FAT 32), then 5 GB Ubuntu (ext3) and 5 GB home partition /hda6 (ext3) and finally swap partition.
I can access the data on the FAT 32 partition no problems . can I install Ubuntu again on the master Hard Drive, and not only access /hda6 on the slave, but also add the slave drive as a boot option when GRUB loads?
If this is impractical however, and there is a simpler/better way to solve this please let me know
(such as lha's post [http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880) ) 
THANKS guys/gals



:)

---

### Post by aysiu on 2006-04-08
Yes, yes, and yes.

Be sure to choose "Manually edit partition table" during installation.

Make sure you choose your /home partition to be /home but **not** formatted. And make sure you install Grub to the MBR.

---

### Post by carverj on 2006-04-08
So does that mean I can manually edit the partitions and choose /home, but not format, then boot into Ubuntu (master), then edit menu.list.
oh, and I am used to using the fstab edit, /hda6 /home ext3 defaults 0 2
would I have to enter something like /hd1/hda6 /home ext3 defaults 0 2 to link my master Ubuntu with the slave home partition?
sorry for needing it spelled out
:-D

---

### Post by aysiu on 2006-04-09
[QUOTE=carverj]So does that mean I can manually edit the partitions and choose /home, but not format,[/quote] Yes. In fact, that's what you *should* do. > then boot into Ubuntu (master), then edit menu.list. No. Just follow through with the installation. When you're asked if you want to install Grub to the MBR, say "yes."

---

### Post by carverj on 2006-04-09
ok, so  /hd1/hda6 /home ext3 defaults 0 2 is the correct fstab edit and no post install grub tampering required. I should be able to use my original home partition (slave drive) as backup for linux, and use the new master drive as a dual boot XP/ Ubuntu drive where home is installed on the same partition as the Ubuntu root and ext3 filesystem
please let me know if I've missed something as I've never actually used /home in this way. 
THANKS very much mate

:D

---

### Post by carverj on 2006-04-10
Actually that doesn't look right does it
> ok, so /hd1/hda6 /home ext3 defaults 0 2 is the correct fstab edit 
or is it something like /dev/hdb6 /home ext3 defaults 0 2
:confused:

---

### Post by carverj on 2006-04-11
tried installing ubuntu on master drive (/hda5), do I set the mount point as / or is /media/hda5 ok as the mount point?

---

### Post by Rasymas on 2006-04-11
Sorry for being ignorant, but how can I add back the option in PC loading screen where I can choose what OS i'd like to run now.. XP or Ubuntu.. few days ago my windows broked down.. so I reinstalled them... but I can't access Ubuntu right now... Any solutions?

Thanks in advance ;)

Later ;)

---

### Post by carverj on 2006-05-29
G'day mate,
                    just install grub to the master boot record. It helps if Windows is at the start of the disk (installed first). That way Linux will recognise Windows and display on the boot load screen.
Hop e I have been helpful here.

---


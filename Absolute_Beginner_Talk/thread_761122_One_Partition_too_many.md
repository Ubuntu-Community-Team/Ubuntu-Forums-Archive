---
title: "One Partition too many"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by osabr22000 on 2008-04-20
I had installed Ubuntu on my Toshiba and could boot either XP Home or Ubuntu.  After I tried to install Compiz Fusion, I was unable to successfully boot Ubuntu again.  I didn't know what the issue could be so I figured the easiest way to fix the problem would be to reinstall Ubuntu over the ruined partition.  Instead the second Ubuntu install created a second partition.  How do I delete that ruined Ubuntu and split that partition between XP home and the functioning Ubuntu partition?  When explaining, please keep in mind I know next to nothing about Linux....

Thank you for any help you can give.

---

### Post by alpdo on 2008-04-20
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by alpdo on 2008-04-20
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Victormd on 2008-04-20
Keep in mind that you may have to re-direct grub to boot from the proper partitions (you're changing the number of partitions, therefore, the partition ID). It's not as straight forward as it might sound...
Download gparted live CD and the super grub disk ([http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)  or  [http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml))

1. burn the super grub disk (you might not need this, but if you do, you won't have access to it afterwards, you'll see why)
2. burn Gparted and boot from the gparted CD;
3. BACKUP ALL YOUR DATA
4. delete the partition you don't want (this is all graphical so don't worry);
5. resize the XP and Ubuntu partitions to the size you want.

Once the modifications are applied, reboot. If you don't get any errors, great! forget about super grub, but if you get a grub error, fire up the super grub disk and follow the instructions to re-setup your grub...

---


---
title: "Booting Ubuntu From Command Line."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Eclipse. on 2007-03-10
For a while now I had been using Ubuntu, Xp and Vista and was using the ubuntu boot loader fine but last night I installed Sabayon to try it out after a friend recomened it to me.Now however there is no option to boot ubuntu at the boot screen.I get the Sabayon boot screen, it only gives me the choice of Sabayon and the Vista boot loader.I'm guessing theres a command you can type to boot from it as there is the option to use command line but I dont know what it is because I'm still a bit of a n00b with linux.Could someone help me please.:)

---

### Post by yabbadabbadont on 2007-03-10
Open a terminal window on Sabayon and run "fdisk -l"  (you'll need to either use sudo or su to root first).  Please post the output as well as the contents of your /etc/fstab file.

---

### Post by Eclipse. on 2007-03-10
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS               (Xp)
/dev/sda2            5100        9964    39078112+   f  W95 Ext'd (LBA)         (Four Partitions Below)
/dev/sda5            5100        6374    10241406    7  HPFS/NTFS               (Vista)
/dev/sda6            6375        6437      506016   82  Linux swap / Solaris    (Swap)
/dev/sda7            6438        8689    18089158+  83  Linux                   (Ubuntu)
/dev/sda8            8690        9964    10241406   83  Linux                   (Sabayon)


/ect/fstab File -

/dev/sda8               /                       ext2    defaults        1 1
/dev/sda6               swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0

---

### Post by Eclipse. on 2007-03-10
Could someone help me plz.:lolflag:

---

### Post by pveith on 2007-03-10
i suppose you haven't deletet your Ubuntu installation. So boot Sabayon, mount your Ubuntu partition. You will have a menu.lst on your Ubuntu Partiont <Ubuntu-Mount-Point>/boot/grub/menu.lst at the very end of the file you will find some entries, which start your Ubuntu system. cut and paste these to the /boot/grub/menu.lst file of Sabayon. Reboot and rejoice. Ubuntu should work again then...

---


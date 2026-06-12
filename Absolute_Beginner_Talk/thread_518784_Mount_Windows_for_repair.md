---
title: "Mount Windows for repair"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by AngelBreath on 2007-08-06
Hi everyone. 
I have a dual boot machine with windows vista and ubuntu. This is my fdisk -l output

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6375       12749    51200000    7  HPFS/NTFS
/dev/sda3           12749       20023    58433536    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11754    94413973+   7  HPFS/NTFS
/dev/sdb2           17578       30515   103924485    f  W95 Ext'd (LBA)
/dev/sdb3   *       11755       17577    46773247+  83  Linux
/dev/sdb5           17832       30515   101884198+   7  HPFS/NTFS
/dev/sdb6           17578       17831     2040192   82  Linux swap / Solaris

Partition table entries are not in disk order

So i m going to Places-->computer-->windows (i can see a disk named like this here) and taking this message:

Unable to mount the volume 'Windows'.

How can i see my windows partition?

I m new to Linus so i m a little confused about what to mount in command prompt. I saw this [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585) but confused a little.
I ll aprisiate for any help 

Thanks in advance

---

### Post by alienexplorers on 2007-08-06
Follow the directions on this page;
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by AngelBreath on 2007-08-06
Thanks a lot ,that works but i cant have access to delete some things i want. Any way to have write access in windows from linux?

---

### Post by Inxsible on 2007-08-06
> **AngelBreath said:**
> Thanks a lot ,that works but i cant have access to delete some things i want. Any way to have write access in windows from linux?

Do you have ntfs-3g installed ? You need that you have write access to NTFS filesystem thru Linux.

Applications --> Add Remove Search for "ntfs" without the quotes. Install NTFS Configuration Tool.

After installation, Go to Applications--> System Tools --> NTFS Configuration Tool and enable write access to Internal and external drives.

---

### Post by alienexplorers on 2007-08-06
You need another program loaded called ntfs???.  I am not sure of the name, but if you do a search for reading and writing to a NTFS partition the program name should be listed.

Inxsible, You beat me to it.

---

### Post by Inxsible on 2007-08-06
> **alienexplorers said:**
> Inxsible, You beat me to it. :D
We are all here to help and learn at the same time :)

---

### Post by AngelBreath on 2007-08-06
Mounting /media/Windows failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/Windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/Windows ntfs-3g defaults,force 0 0

The problem is that i have problem with Alcohol 120% installation. After installing it ,its trying to install a driver that gives me a blue screen in vista. So i m trying to make something by accessing windows from Ubuntu but no luck.

---


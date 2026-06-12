---
title: "NTFS volumes disappeared"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by tamcdonald on 2007-11-18
Alright, everything seemed to be working fine earlier. I've been able to read/write to my NTFS volumes just fine until now. I re-booted into Vista earlier and then when I came back to Ubuntu all of my hard drives are gone except the one Ubuntu is on. The only change I made was I plugged in a USB speakphone device that only works in WIndows. I've unplugged it and restarted with no success. Any suggestions?

---

### Post by MegaJim on 2007-11-18
Do you have the ntfs configuration tool installed? (System Tools -> NTFS Configuration Tool)

If not you can apt-get it and see what happens

```
sudo apt-get install ntfs-config
```

It should detect your ntfs vols for you when run, if not come back and let us know so we can look into the problem in more detail!

Good luck

---

### Post by tamcdonald on 2007-11-18
Yes I do have that installed. Thats how I got read/write support enabled. Running again doesn't seem to do anything.

---

### Post by MegaJim on 2007-11-18
Oh dear!

can you post the output of this command please

```
sudo fdisk -l
```

---

### Post by tamcdonald on 2007-11-18
Disk identifier: 0x5fe52608

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       22902   183947072+   7  HPFS/NTFS
/dev/sda6           22903       22963      489951   82  Linux swap / Solaris
/dev/sda7           22964       30401    59745703+  83  Linux

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28e328e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20022   160826683+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63b563b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19458   156288045    7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sdd: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 912 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1           3       96264    0  Empty
/dev/sdd2               4         912    29206170    b  W95 FAT32

---

### Post by MegaJim on 2007-11-18
What happens if you try to mount one of your NTFS partitions?  Lets say /dev/sda5.

---

### Post by monte48lowes on 2007-11-18
Reboot into vista. Then shutdown cleanly. Finally restart into ubuntu.

If the NTFS drives are not unmounted cleanly, they will not show up under ubuntu.

Mike

---

### Post by tamcdonald on 2007-11-18
I get this

Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sdc5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sdc5 ntfs-3g defaults,force 0 0

---

### Post by MegaJim on 2007-11-18
Do as monte suggests above, then come back to ubuntu and check again.

Also, if you hibernated Vista then this will happen until you do a full shutdown of Vista.

---

### Post by tamcdonald on 2007-11-18
Thanks MegaJIm! All I ended up doing was restarting Vista and shutting down completely. Fixed! Whew.

---

### Post by MegaJim on 2007-11-18
Great, please mark the thread as solved :)

---

### Post by monte48lowes on 2007-11-18
NTFS and ext3 are journaling filesystems. If the drive is not unmounted cleanly the journal will not be written to the file table, but held in the journal. When the drive is mounted the next time, the journal is checked first and written to the file table if necessary. In this case here, the drive was not unmounted cleanly, the linux kernel (smartly, in my opinion) doesn't recognize the drive to prevent corruption of the file table. There is a program that will allow ext3 to be accessed from windows in read/write.

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

With the windows program it is highly recommended to unmount cleanly in linux prior to accessing from windows for the same reasons stated above.

Mike

[http://en.wikipedia.org/wiki/Journaling_file_system]("http://en.wikipedia.org/wiki/Journaling_file_system")

---


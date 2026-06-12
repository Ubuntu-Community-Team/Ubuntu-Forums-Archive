---
title: "[SOLVED] Using my other partition"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Vic! on 2008-04-20
how can i change the permissions on a partition i made when first insalling my system so that i can store things in it. its located at computer:/// 

thank you!!
v

---

### Post by lswest on 2008-04-20
can you post the output of ```
sudo fdisk -l
``` and then tell us exactly what you've done so far to write to the drive?  if it's located at computer:/// chances are you haven't mounted it yet, else it would be in /media/ or /mnt/.

---

### Post by Vic! on 2008-04-20
> v@v-laptop:~$ sudo fdisk -l
[sudo] password for v:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x326f3ad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        4864    19535040   83  Linux
/dev/sda3            4865        5059     1566337+  82  Linux swap / Solaris
/dev/sda4            5060        9729    37511775   83  Linux

Disk /dev/sdb: 1027 MB, 1027416576 bytes
32 heads, 62 sectors/track, 1011 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      392206      967564   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(392205, 19, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(967563, 8, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       85025     1060846   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(85024, 30, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1060845, 20, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      942481     1918302   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(942480, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1918301, 7, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1454477     1454505       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1454476, 12, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1454504, 11, 33)
Partition 4 does not end on cylinder boundary.


thats the out put and you are right, its not mounted. i never assigned a mount point for it it was going to be for WINE but now i just want to use it 

Thanx!

---

### Post by lswest on 2008-04-21
well, if you double-click the icon in computer:/// it should mount it.  If not, you can mount it with: ```
sudo mkdir /media/sda4
sudo mount -t ext3 /dev/sda4 /media/sda4
``` and if that works (here i was assuming sda4 is the drive you're planning on mounting, but if it's not, just change those letters to the partition you want to mount, and in the last line i assume it's formatted as ext3, change that if my assumption is wrong), you can make it mount automatically by adding an entry to fstab (i can post how to do that if you need, but check to make sure it mounts manually first).

---

### Post by Vic! on 2008-04-21
well it mounted when i double clicked it . it showed up as a drive in my dektop and everything... is this the same? now it wont let me drop files in it though it says i dont have privileges for that.

---

### Post by lswest on 2008-04-21
well, what folder does it open?  check what the permissions are, if it says it's only read access to other, change that to read and write, that should fix your problem.

---

### Post by Vic! on 2008-04-21
What do you mean by what folder does it open? I went to my computer:/// then clicked on   38.5 GB Volume ..theres a password prompt i enter it then it goes to /media/disk. thats when i right click>properties>permissions tab and i see that its owned by root and i have no privileges other than access. id like to be able to store photos or media in here will that be possible?


Thanks again! :D

---

### Post by logos34 on 2008-04-21
> **Vic! said:**
> What do you mean by what folder does it open? I went to my computer:/// then clicked on   38.5 GB Volume ..theres a password prompt i enter it then it goes to /media/disk. thats when i right click>properties>permissions tab and i see that its owned by root and i have no privileges other than access. id like to be able to store photos or media in here will that be possible?

try

sudo chown -R yourusername /media/disk

sudo chmod -R 777 /media/disk

---

